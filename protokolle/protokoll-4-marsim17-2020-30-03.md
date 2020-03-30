# Protokoll LA1/SX 3AHME (2019/20)

* **Thema:** Deamons
* **Datum:** 30.03.2020
* **Gefehlt:** -
* **Erstellt von:** Marcher Simon
* **Protokoll letzte Einheit:** [Protokoll 23.03.2020](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/marsim17/protokolle/protokoll-3-marsim17-2020-23-03.md)
---------

## Begriffserklärung
### Deamons unter Linux
Unter Linux werden Prozesse vom Kernel in 3 Unterkategorien geteilt: Interaktive Prozesse, Bash-Prozesse und [Deamons](https://en.wikipedia.org/wiki/Daemon_(computing)#Unix-like_systems). Deamons sind Hintergrundprozesse, die von anderen Prozessen benötigt werden. Sie werden automatisch beim Booten gestartet und werden erst beim Herunterfahren wieder beendet.

### Deamons unter Java
Ein Deamon Thread in Java ist ein spezieller Thread, der die JVM nicht daran hindert zu schließen. Auf der anderen Seite gibt es die High-Priority Threads, die zuerst schließen müssen bevor die JVM es tun kann. Alle Threads innerhalb der main() Methode sind zum Beispiel High-Priority Threads. Ein Beispiel eines Deamons-Threads ist der Garbage Collector. 

## Erstellen eines eigenen Deamons
### Programm erstellen
Der C-Quellcode für den Deamons ist:
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

Zum Erstellen des Programs muss man folgende Vorgehensweise befolgen:  
  Ins gesünschte Verzeichnis wechseln  
  `mkdir mydeamon && cd mydeamon`  
  `touch mydeamon.c && nano mydeamon.c`  
  Mit `Ctrl`+`Shift`+`V` kann der Quelltext aus der Zwischenablage eingefügt werden.  
  Mit `Ctrl`+`S` speichert man und mit `Strg`+`X` schließt man den Editor.  
  `gcc -o mydeamon mydeamon.c`  
  
Zum Testen des Programms muss man `./mydeamon` ausführen. Das Ergebnis nach 6 Sekunden sollte folgendermaßen aussehen:  
```console
[simon@simon mydeamon]$ ./mydeamon 
Hello 1
Hello 2
Hello 3
Hello 4
```
Nach dem Beenden sollten auch die Nachrichten im Log stehen. Das kann man mit dem Befehl `journalctl` überprüfen. Brauchbare Parameter sind `-f` um die Daten live auszugeben, `-p 4`, um nur Warnungen anzuzeigen, `-o verbose`, um mehr Informationen anzeigen zu lassen und `-u name`, um einen bestimmten Deamon zu beobachten. Weitere Informationen findet man unter `man journalctl`.  
Der Output von `journalctl -f` ist unter anderem:  
```console
Mar 30 17:05:55 simon mydaemon[5684]: mydaemon started.
Mar 30 17:06:01 simon mydaemon[5684]: bin bei der letzten Ausgabe...
Mar 30 17:06:01 simon mydaemon[5684]: mydaemon terminated.
```

Optional kann die Log Datei auch mit `tail -f /var/log/syslog` ausgegen werden . `-f` bedeutet hier, dass der Output mit der Datei synchronisiert bleibt.  

### systemd Service erstellen
systemd ist selbst ein Deamon-Prozess. Er wird auch init-Prozess genannt und wird als erstesr Prozess (PID 1) gestartet, um alle anderen Prozesse zu starten, zu überwachen und zu beenden. Er wurde entwickelt um verschiedene Linux-Systeme zu vereinheitlichen und vereinfachen. Um mydeamon, das bis jetzt nur ein gewöhnliches Programm war zu einem Deamon zu machen, muss man es zu systemd hinzufügen. Dafür wird zuerst mit `touch mydeamon.service` eine neue Datei erstellt, in der man, wie bereits zuvor, den folgenden Code kopieren muss. (Der Pfad muss angepasst werden)  
```console
[Unit]
Description=my background program for testing system services

[Service]
ExecStart=PfadZuMyDeamon/mydaemon
IgnoreSIGPIPE=false
KillMode=process
```
[`ExecStart`](https://www.freedesktop.org/software/systemd/man/systemd.service.html#ExecStart=) gibt den Pfad des zu ausführenden Programs an.  
[`IgnoreSIGPIPE`](https://www.freedesktop.org/software/systemd/man/systemd.exec.html#IgnoreSIGPIPE=) - Ein Sigpipe ist ein Signal, das einem Prozess gesendet wird, wenn es versucht in eine [Pipeline](https://de.wikipedia.org/wiki/Pipeline_(Unix)) zu schreiben, die nicht für read geöffnet ist. Im Normalfall bewirkt ein Sigpipe die Beendigung des Programms.  
[`KillMode`](https://www.freedesktop.org/software/systemd/man/systemd.kill.html#KillMode=) bestimmt welche weiteren Prozesse beim Beenden des Deamons noch beendet werden. Bei `process` wird nur der Hauptprozess beendet.

Als nächstes muss man mit `sudo ln -s PfadZuMyDeamon/mydeamon.service /etc/systemd/system/mydeamon.service` die Datei verlinken. Der `-s` Parameter gibt an, dass es sich um einen Softlink handelt.

### Service ausführen und überwachen
Mit `sudo systemctl start mydeamon` kann man den Deamon starten. Anschließend erhält man mit `sudo journalctl -f -u mydeamon` folgende Ausgabe:  
```console
-- Logs begin at Sat 2020-01-25 17:00:55 CET. --
Mar 30 17:55:30 simon systemd[1]: Started my background program for testing system services.
Mar 30 17:55:30 simon mydeamon[7291]: Hello 1
Mar 30 17:55:30 simon mydaemon[7291]: mydaemon started.
Mar 30 17:55:32 simon mydeamon[7291]: Hello 2
Mar 30 17:55:34 simon mydeamon[7291]: Hello 3
Mar 30 17:55:36 simon mydaemon[7291]: bin bei der letzten Ausgabe...
Mar 30 17:55:36 simon mydeamon[7291]: Hello 4
Mar 30 17:55:36 simon mydaemon[7291]: mydaemon terminated.
Mar 30 17:55:36 simon systemd[1]: mydeamon.service: Succeeded.
```
"my background program for testing system services" ist hier die Beschreibung in der mydeamon.service Datei.  
Mit `sudo systemctl restart mydeamon` kann der deamon neu gestartet und falls Ängerungen der Service-Datei kann mit `sudo systemctl deamon-reload` eine Aktualisierung durchgeführt werden. Mit `sudo systemctl stop mydeamon` kann der Deamon beendet werden. Mit `sudo systemctl status mydeamon` erhält man sehr übersichtliche Informationen des Deamons, die wie folgt aussieht:  
```console
● mydeamon.service - my background program for testing system services
     Loaded: loaded (PfadZuMyDeamon/mydeamon.service; linked; vendor preset: disabled)
     Active: active (running) since Mon 2020-03-30 18:04:33 CEST; 5s ago
   Main PID: 7509 (mydeamon)
      Tasks: 1 (limit: 9424)
     Memory: 156.0K
     CGroup: /system.slice/mydeamon.service
             └─7509 PfadZuMyDeamon//mydeamon

Mar 30 18:04:33 simon systemd[1]: Started my background program for testing system services.
Mar 30 18:04:33 simon mydaemon[7509]: mydaemon started.
Mar 30 18:04:33 simon mydeamon[7509]: Hello 1
Mar 30 18:04:35 simon mydeamon[7509]: Hello 2
Mar 30 18:04:37 simon mydeamon[7509]: Hello 3
Mar 30 18:04:39 simon mydaemon[7509]: bin bei der letzten Ausgabe...
Mar 30 18:04:39 simon mydeamon[7509]: Hello 4
Mar 30 18:04:39 simon mydaemon[7509]: mydaemon terminated.
Mar 30 18:04:39 simon systemd[1]: mydeamon.service: Succeeded.
```

### Autostart
Beim Starten des Systems müssen alle Deamons zum richtigen Zeitpunkt gestartet werden. Wenn man seinen Deamon automatisch starten lassen will muss man also den Startzeitpunkt in der Service-Datei hinzufügen. Der zusätzliche Eintrag lautet:  
```console
[Install]
WantedBy=multi-user.target
```
"multi-user.target" bedeutet, dass der Deamon gestartet sein muss, bevor das System Muli-User fähig ist. Mit `sudo systemctl enable mydeamon` wird der Dienst zum Autostart hinzugefügt. Versucht man diesen Befehl ohne den [Install]-Eintrag erhält man folgende Fehlermeldung:  
```console
The unit files have no installation config (WantedBy=, RequiredBy=, Also=,
Alias= settings in the [Install] section, and DefaultInstance= for template
units). This means they are not meant to be enabled using systemctl.
 
Possible reasons for having this kind of units are:
• A unit may be statically enabled by being symlinked from another unit's
  .wants/ or .requires/ directory.
• A unit's purpose may be to act as a helper for some other unit which has
  a requirement dependency on it.
• A unit may be started when needed via activation (socket, path, timer,
  D-Bus, udev, scripted systemctl call, ...).
• In case of template units, the unit is meant to be enabled with some
  instance name specified.
```

Um den Deamon besser und jederzeit überwachen zu können, wird das Programm folgendermaßen abgeändert:
```C
#include <stdio.h>
#include <stdlib.h>
#include <syslog.h>
#include <unistd.h>

int main () {
	
	while(1) {

		openlog ("mydaemon", LOG_PID, LOG_DAEMON);
		syslog (LOG_NOTICE, "mydaemon started.");
		closelog();
	
		printf("Hello 1\n"); fflush(stdout);
		sleep (2);
		printf("Hello 2\n"); fflush(stdout);
		sleep (2);
		printf("Hello 3\n"); fflush(stdout);
		sleep (2);
	
		openlog ("mydaemon", LOG_PID, LOG_DAEMON);
		syslog(LOG_WARNING, "bin bei der letzten Ausgabe...");
		closelog();
	
		printf("Hello 4\n"); fflush(stdout);
		usleep(1000);
	
		openlog ("mydaemon", LOG_PID, LOG_DAEMON);
		syslog (LOG_NOTICE, "mydaemon terminated.");
		closelog();
		usleep(1000);
	}
	
    return 0;
}

}
```
Damit erfolgen die Ausgaben in einer Endlosschleife. Der Sourcecode muss natürlich neu kompiliert werden.  
Mit `sudo reboot` startet man das System neu und mydeamon wird gestartet.
