# Protokoll 11.05.2020 Pfanner
* **Thema:** Daemons: Grundlagen und Anwendung
* **Datum:** 11.05.2020
* **Gefehlt:** -
* **Erstellt von:** Pfanner Jan

## Inhaltsverzeichnis
* [Was ist ein Daemon?](#was-ist-ein-daemon)
* [Erstellen eines eigenen Daemons](#erstellen-eines-eigenen-daemons)
* [Überprüfen und Überwachen des Daemons](#überprüfen-und-überwachen-des-daemons)
* [Autostart](#autostart)

## Was ist ein Daemon?
Ein Daemon (auch Dämon) ist ein Prozess, der von einem Betriebssystem im Hintergrund ausgeführt wird. Im Gegensatz zu herkömmlichen Prozessen interagiert er nicht mit dem user, sondern stellt nur Dienste für andere Prozesse bereit.

## Erstellen eines eigenen Daemons
Ursprünglich war als Übung das Erstellen eines Daemons auf einem Raspberry Pi vorgesehen. Aufgrund der Umstände musste darauf jedoch verzichtet werden. Daher haben wir unseren Dameon in Ubuntu 20.04 folgendermaßen erstellt: 

Der auszuführende Code als C-Programm, genannt **mydaemon.c**, war folgender:
```C
#include <stdio.h>
#include <stdlib.h>
#include <syslog.h>
#include <unistd.h>

int main () {
    openlog ("mydaemon", LOG_PID, LOG_DAEMON);

    syslog (LOG_NOTICE, "mydaemon started.");
    printf("Hello 1\n"); fflush(stdout);
    sleep (2);
    printf("Hello 2\n"); fflush(stdout);
    sleep (2);
    printf("Hello 3\n"); fflush(stdout);
    sleep (2);
    syslog(LOG_WARNING, "bin bei der letzten Ausgabe...");
    printf("Hello 4\n"); fflush(stdout);

    usleep(1000);
    syslog (LOG_NOTICE, "mydaemon terminated.");
    closelog();
    usleep(1000);

    return 0;
}
```
Alle als Befehl gekennzeichneten Segmente sind in der Ubuntu Shell (dem Terminal) auszuführen. Verzeichnis- und Dateinamen können mit Autovervollständigung per Tabulatortaste einfacher eingegeben werden.

Mit dem Befehl `mkdir mydeamon` wird das Verzeichnis für den Daemon erstellt. Der Befehl `cd mydeamon` navigiert in dieses Verzeichnis.
Mit `nano mydeamon.c` wird der Texteditor nano aufgerufen, um eine Datei mit dem Namen mydaemon.c zu erstellen. Nun kann man in der Shell den obigen Quellcode einfügen und den Editor mit CTRL+X schließen. Das Kopieren von Text in der Shell funktioniert mit CTRL+V nicht, CTRL+Shift+V oder rechtsklick-paste gehen jedoch. Ist das Programm an Ort und Stelle, muss es noch mit `gcc -o mydaemon mydaemon.c` kompiliert werden. Ruft man nun `ls -l` auf und sieht zwei Dateien, mydaemon und mydaemon.c, hat man diesen Schritt erfolgreich gemeistert.
Noch immer im Verzeichnis mydaemon ist es nun möglich, das Programm mit dem Befehl `./mydaemon ` zu starten. Wer sich den C-Code angesehen hat, wird erkennen, dass auf der Konsole lediglich 4-mal Hello in zweisekündigen Abständen ausgegeben wird. Erhält man dies
```console
jan@jan-VirtualBox:~/mydaemon$ ./mydaemon
Hello 1
Hello 2
Hello 3
Hello 4
jan@jan-VirtualBox:~/mydaemon$ 
```
als Ausgabe, funktioniert das Programm ordnungsgemäß.

## Überprüfen und Überwachen des Daemons
Dies macht jedoch nicht den gesamten Umfang von mydaemon.c aus. Wie man erkennen kann, wird durch die syslog()-Befehle Text an den Log übergeben. Diesen kann man mit dem Befehl `journalctl` einsehen. Für diesen gibt es verschiedene Optionen.

`journalctl -f` erzeugt eine kontinuierliche Ausgabe (follow), die mit CTRL+C abgebrochen werden kann. Der Teil dieser Ausgabe, der unser Programm betrifft, sieht so aus:


```console
Mai 12 08:51:03 jan-VirtualBox mydaemon[2407]: mydaemon started.
Mai 12 08:51:09 jan-VirtualBox mydaemon[2407]: bin bei der letzten Ausgabe...
Mai 12 08:51:09 jan-VirtualBox mydaemon[2407]: mydaemon terminated.
```
Wie man sieht, sind die dem syslog übergebenen Meldungen am syslog angekommen.

`journalctl -f -p 4` , zuzüglich zu -f werden mit `-p 4` (priority 4) nur Meldung der Priorität 4, also Warnungen, ausgegeben.

`journalctl -f -v verbose` Verbose gibt zusätzliche Informationen aus (man-Eintrag: shows the full-structured entry items with all fields).

`tail -f /var/log/syslog` Der Befehl tail gibt den Schlussteil einer Datei (die letzten 10 Zeilen laut man) auf der Shell aus. Die Addition von -f sorgt dafür, dass der tail-Befehl der Datei auch dann noch "folgt", wenn diese umbenannt wird. Dieser Befehl gibt ebenfalls den syslog wieder, nur in diesem Fall durch Zugriff auf dessen Speicherort.

## Anhängen des Programmes an systemd
Systemd ist ein Prozess zur Verwaltung der Startvorgänge aller anderen Prozesse. Im Gegensatz zu seinen Vorgängern arbeitet es nach dem Prinzip, units nur bei Bedarf (d.h. bei Abhängigkeit durch eine andere unit) zu starten. Mit dem bereits kennengelernten Befehl `systemctl` kann auf die Steuerdateien zugreifen und diese verändern bzw. überwachen. 

Da unser Programm mydaemon bislang nur bei manueller Ausführung arbeitet, ist es noch **kein Daemon**. Dafür müssen folgende Schritte befolgt werden:

Im Verzeichnis /home/user/mydaemon (Achtung! user -> eigentlicher username!) ist eine Datei mydaemon.service anzulegen, dies geschieht mit `touch mydaemon.service`. Nun öffnet man diese mit `nano mydaemon.service` und fügt folgendes ein:

```
[Unit]
Description=my background program for testing system services

[Service]
ExecStart=/home/user/mydaemon/mydaemon
IgnoreSIGPIPE=false
KillMode=process
```
Auch hier aufpassen: **user durch den eigenen username ersetzen!**

ExecStart bezeichnet Kommandos, die beim Starten des Services ausgeführt werden. Das erste Argument muss, wie oben, ein Pfad zu einer ausführbaren Datei oder ein simpler Dateiname sein. [Quelle](https://www.freedesktop.org/software/systemd/man/systemd.service.html#ExecStart=)

IgnoreSIGPIPE=false sorgt dafür, dass das von einem Prozess gesendete Signal SIGPIPE nicht ignoriert wird. [Quelle](https://www.freedesktop.org/software/systemd/man/systemd.exec.html#IgnoreSIGPIPE=)

KillMode=process definiert die Terminierung des Prozesses. Mit process wird nur der Hauptprozess "gekillt". [Quelle](https://www.freedesktop.org/software/systemd/man/systemd.kill.html#KillMode=)

Nun muss im Ordner /etc/systemd/system von systemd ein Link auf unser mydaemon erstellt werden. 
Dafür geben wir uns superuser-Rechte mit `sudo -i` und wechseln ins richtige VErzeichnis mit `cd /etc/systemd/system`. Nun wird mit dem Befehl `ln -s /home/user/mydaemon/mydaemon` (letzte Warnung: user -> eigener username) ein Link (Symbolic link durch -s) zu unserem Programm erzeugt. Sieht man sich das Verzeichnis mit `ls -l` an, kann man diesen auch sehen. Im Ubuntu-Terminal kennzeichnet eine rote Färbung einen toten Link. In diesem Fall sollte man den Link löschen und erneut erstellen, diesmal richtig. Mit `exit` verlässt man den superuser-Modus wieder.

Damit kann man den Dienst mit `sudo systemctl start mydaemon` starten und in einer anderen Shell die Überwachung mit `sudo journalctl -f -u mydaemon` vornehmen. Startet man nun den Dienst erneut (mit den Pfeiltasten können früher ausgeführte Befehle eingefügt werden) kann man die Ausführung live beobachten. Dies sieht so aus:
```console
Mai 12 10:11:15 jan-VirtualBox systemd[1]: Started my background program for testing system services.
Mai 12 10:11:15 jan-VirtualBox mydaemon[3344]: mydaemon started.
Mai 12 10:11:15 jan-VirtualBox mydaemon[3344]: Hello 1
Mai 12 10:11:17 jan-VirtualBox mydaemon[3344]: Hello 2
Mai 12 10:11:19 jan-VirtualBox mydaemon[3344]: Hello 3
Mai 12 10:11:21 jan-VirtualBox mydaemon[3344]: bin bei der letzten Ausgabe...
Mai 12 10:11:21 jan-VirtualBox mydaemon[3344]: Hello 4
Mai 12 10:11:21 jan-VirtualBox mydaemon[3344]: mydaemon terminated.
Mai 12 10:11:21 jan-VirtualBox systemd[1]: mydaemon.service: Succeeded.
```
Wie man sieht, ist die Bezeichnung des Daemons die Beschreibung in mydaemon.service. Etwaige Fehler lassen sich durch ein Neuladen mittels `sudo systemctl daemon-reload` beheben.

Mit diesen Schritten ist mydaemon endlich ein vollwertiger Daemon. Dazu gibt es noch ein paar nützliche Befehle:

`systemctl start mydaemon` , bereits gesehen, started den Daemon

`systemctl restart mydaemon` veranlasst einen Neustart des Daemons

`systemctl stop mydaemon` beendet den Daemon

`systemctl status mydaemon` gibt Informationen über den Daemon aus

## Autostart
Möchte man seinen Daemon per Autostart ausführen lassen, geht das so:

Der Befehl dafür lautet `sudo systemctl enable mydaemon`. Doch dies alleine führt bloß zu einer Fehlermeldung. Durch das Einfügen von
```
[Install]
WantedBy=multi-user.target
```
 in die Datei mydaemon.service wird vermittelt, dass mydaemon beim Eintritt in Phase der Multi-User-Fähigkeit gestartet werden soll. Mit dieser getroffenen Maßnahme kann mydaemon nun mit dem obigen Befehl in den Autostart eingegliedert werden. Startet man den Rechner neu (dies geht aus der Shell mit `reboot` oder `sudo reboot`), kann die Ausführung von mydaemon überprüft werden.
