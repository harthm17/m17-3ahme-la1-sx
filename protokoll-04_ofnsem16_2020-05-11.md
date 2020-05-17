# 4. Protokoll
---------------------------------------------
## Thema: Dienste in Linux
---------------------------------------------
* Datum:      11.05.2020
* Gruppe:     3
* Abwesend:   keiner
* Verfasser:  Ofner Sebastian
* Klasse:     3AHME/AHME17
* Schuljahr:  2019/20
---------------------------------------------
## Inhaltsverzeichnis
* [Vorraussetzungen](#vorraussetzungen)
* [Unterlagen durcharbeiten](#unterlagend-durcharbeiten)
* [Erstellen eines Dämons](#erstellen-eines-dämons)
---------------------------------------------
### Vorraussetzungen
Vorraussetzungen sind der Inhalt der Linux-Grundkenntnisse und ein Ubuntu-System 20.04

### Unterlagen durcharbeiten
Zwei Skripte waren durchzuarbeiten (lesen, verstehen), um die Grundlagen der Übung zu bekommen

Hier das [erste Skript](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#155470713 )

Hier das [zweite Skript](https://wiki.ubuntuusers.de/systemd/)

### Erstellen eines Dienstes (Dämon)
Dämon: Programm im hintergrund, stellt Dienste zu verfügung

#### Übung
Wir sollten die Übung eins aus dem ersten Skript machen. Darin geht es um die 
Erstellung eines Dienstes die ein C-Programm ausführt. Es soll alle 2 Sekunden einen Text ausgeben

Als erstes war das CProgramm zu erstellen:
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

Danach übersetzten wir das Programm mit dem GNU-Compiler
Dazu benutzten wir folgende Befehle:
```
user@pi:~$ mkdir mydaemon                        // neuer Ordner
user@pi:~# cd mydaemon                           // Ordner wählen
user@pi:~/mydaemon $ nano mydaemon.c             // Textedidor öffnen
user@pi:~/mydaemon $ gcc -o mydaemon mydaemon.c  // übersetzen mit GNU-Compiler
user@pi:~/mydaemon $ ls -l
```

Danach testesten wir das Programm indem wir es mit ```./mydaemon``` ausführten
Es sollte so aussehen:
```
Hello 1
Hello 2
Hello 3
Hello 4
```

Als nächstes erstellten wir die **mydaemon.service** mit dem Inhalt:
```
[Unit]
Description=my background program for testing system services

[Service]
ExecStart=/home/user/mydaemon/mydaemon
IgnoreSIGPIPE=false
KillMode=process
```

Jetzt erstellen wir in /etc/systemd/system einen Link auf unsere Service-Datei:
```
user@pi: ~/mydaemon$ sudo -i
root@pi: ~# cd /etc/systemd/system
root@pi: /etc/systemd/system# ln -s /home/user/mydaemon/mydaemon
root@pi: /etc/systemd/system# ls -l
...
lrwxrwxrwx 1 root root   40 Mär 29 15:23  mydaemon.service -> /home/user/mydaemon/mydaemon.service
...
root@pi: /etc/systemd/system# exit
user@pi: ~/mydaemon$ 
```

Danach sollten wir den Dienst Starten:
```
user@pi: ~/mydaemon$ sudo systemctl start mydaemon
user@pi: ~/mydaemon$ 
```

#### Autostart
Um einen Autostart durchführen zu können muss in der Servicedatei etwas hinzugefügt werden:
```
[Install]
WantedBy=multi-user.target
```

Danach müssen wir diese Befehle in die Konsohle eingeben:
```
user@pi: ~/mydaemon$ sudo systemctl enable mydaemon
user@pi: ~/mydaemon$ sudo reboot
```
Jetzt sollte man sehen ob der Dienst funktioniert.
