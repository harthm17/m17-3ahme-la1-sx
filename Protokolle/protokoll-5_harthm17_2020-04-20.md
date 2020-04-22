# 5. Protokoll
---------------------------------------------
## Thema: Dienste in Linux Systemen (2)
---------------------------------------------
* Datum:      21.04.2020
* Gruppe:     2  
* Abwesend:   keiner
* Verfasser:  Thomas Harrer 
* Klasse:     3AHME
* Schuljahr:  2019/20
---------------------------------------------
## Inhaltsverzeichnis
* [Voraussetzungen](#voraussetzungen)
  * [Grundlagen](#grundlagen)
* [Erstellung eines Dienstes](#erstellung-eines-dienstes)
  * [Übung](#übung)
  * [Endlos-Dienst automatisch starten lassen](#endlos-dienst-automatisch-starten-lassen)
  * [Wichtige Begriffe](#wichtige-begriffe)

---------------------------------------------
### Voraussetzungen
Um an dieser Übung teilnehmen zu dürfen benötigt man:
* Linux Grundkenntnisse 
* Ubuntu 18.04 System native oder via Virtualisierung (zB Virtualbox)

#### Grundlagen
Wir haben zwei verschiedene Skripta für das erledigen der Übung bekommen.  
  1) Das erste war das **Linux 2** Skriptum, wo wir die Befehle und Übungen vorgegeben haben. In diesem Skriptum haben wir uns auf die Kaptiel 1, 1.1 und 1.3 bezogen, um die Grundlagen zu erlernen.  
-> Um auf das Skrptum zu kommen, klicken Sie [hier](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#155470713 ).

  2) Das andere Skriptum erklärt wichtige Begriffe des Themas.  
-> Um auf das Skrptum zu kommen, klicken Sie [hier](https://wiki.ubuntuusers.de/systemd/)

### Erstellung eines Dienstes
Ein Dämon ist ein Programm, das im Hintergrund abläuft und bestimmte Dienste zur Verfügung stellt, welches auf einem Unix bzw ein unixartiges Systemen läuft.

In Java ist es laut dieser [Website](https://www.dpunkt.de/java/Programmieren_mit_Java/Multithreading/8.html) so:
> Daemon-Threads unterscheiden sich dadurch von normalen Threads (auch User-Threads genannt), dass ihr Status nicht bei der Ermittlung des Beendigungszeitpunkts eines Java-Programms berücksichtigt wird. Andersherum formuliert: Bei der Beendigung jedes User-Threads wird geprüft, ob noch andere User-Threads laufen. Ist das nicht der Fall, wird das Programm beendet, und zwar unabhängig davon, ob noch Daemon-Threads laufen und in welchen Zustand sie sich befinden. 


#### Übung
In dieser Übung sollen wir einen Dienst erstellen, welcher ein C-Programm laufen lässt. Dieses Programm wird im Hintergrund laufen und gibt viermal einen Text aus und zwar alle 2 Sekunden.

Wir haben nach unserem Skriptum **Linux 2** (Kapitel 1.4) gearbeitet.

Der erste Schritt ist es, dass C Programm zu erstellen bzw eine main.c Datei.
Der Quelltext sieht so aus:
```
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

Dannach übersetzten wir das C-Programm in unserem Terminal. Hierbei erstellen wir einen neuen Ordner und eine neue main Datei, wobei die Erstellung der neuen main Datei nicht unbedingt notwendig ist.  
Wir haben folgende Befehle verwendet, mit den Pfeilen wurden die einzelnen Schirtte nochmals genauer erklärt:
```
thomas@thomas-VirtualBox:~$ mkdir mydaemon                <--- neuen Ornder erstellen
thomas@thomas-VirtualBox:~$ cd mydaemon                   <--- in den Ordner reingehen
thomas@thomas-VirtualBox:~$ nano mydaemon.c               <--- Terminal Texteditor öffen und C Programm einfügen
thomas@thomas-VirtualBox:~$ gcc -o mydaemon mydaemon.c    <--- Übersetzten mit GCC Compiler
thomas@thomas-VirtualBox:~$ ls -l  
```
Ist man in Terminal Texteditor drinnen, muss man mit STRG + O (Buchstabe nicht Zahl) und dann ENTER speichern und mit STRG + X für verlassen, drücken.

Nun haben wir einen neuen Ornder angelegt mit einer main.c Datei. Diese können wir mit dem Befehl ```./mydaemon``` ausführen.  
Das ausgeführte Programm sieht dann so aus:

![](https://cdn.discordapp.com/attachments/692432976503373854/694930441769320496/Bild1.png)

Was bedeutet journald?
Dies werde ich mit einem Auszug der Mainpage beschreiben:
> journalctl may be used to query the contents of the systemd(1) journal as written by systemd-journald.service(8). If called without parameters, it will show the full contents of the
journal, starting with the oldest entry collected.


Als Nächstes testen wir unser Programm. Wir können man mit Hilfe von weiteren Shells mit folgenden Befehelen die Ausgabe im Log oder im journald anzeigen lassen.
```
thomas@thomas-VirtualBox:~$ journalctl -f
thomas@thomas-VirtualBox:~$ journalctl -f -p 4
thomas@thomas-VirtualBox:~$ journalctl -f -v verbose
thomas@thomas-VirtualBox:~$ tail -f /var/log/syslog
```

Dannach muss man eine neue Datei erstellen namens "mydaemon.service". 
Wie erstellt man aber eine neue Datei?
Diese kann man im Terminal direkt anlegen. Und öffnet man mit dem Befehl ```nano mydaemon.service``` den Terminaleditor und fügt folgenden Text ein.
```
[Unit]
Description=my background program for testing system services

[Service]
ExecStart=/home/user/mydaemon/mydaemon
IgnoreSIGPIPE=false
KillMode=process
```

Wichtig zu erwähne ist, das dieser Pfad natürlich auf Ihren Gerät nicht funktioniert.
In meinem Fall war das Verzeichnis /home/thomas/mydaemon/mydaemon.


Wenn man diese erstellt hat muss man als Super User einsteigen.
Dies geht mit folgenden Befehlen:  
```
thomas@thomas-VirtualBox:~$ sudo -i
-> [sudo] Passwort für Thomas: 
```



#### Endlos-Dienst automatisch starten lassen


#### Wichtige Begriffe
Die Theoriefragen habe ich schon am Anfang der Unterrichtseinheit ausgearbeitet.
* ExecStart: ExecStart ist der Befehl, der beim Start der Unit ausgeführt wird.

* Ignore SIGPIPE: Wird beim Versuch verschickt, in eine nicht mehr existierende Pipe zu schreiben. (Pipe - "Datenstrom" zwischen zwei Programme)

* KillMode: Legt fest, wie die Prozesse dieser Unit beendet werden soll bzw getötet werden soll. Entweder mit **control-group**, **process**, **mixed** oder **none**.

