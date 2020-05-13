# Protokoll LA1/SX 3AHME (2019/20)

* **Thema:** Erstellung eines Daemons
* **Datum:** 11.05.2020
* **Gefehlt:** -
* **Erstellt von:** Peyer Kassandra

----------------------------------------------------------------------------------------------
## Inhaltsverzeichnis

1. [Was bedeutet Daemon?](#wasbedeutetdaemon?)
2. [Erstellung eines Daemons](#erstellungeinesdaemons)
3. [Erstellung eines Service](#erstellungeinesservice)
4. [Daemon mit Autostart](#daemonmitautostart)

----------------------------------------------------------------------------------------------
## Was bedeutet Daemon?

Ein Daemon ist ein Hintergrundprozess(Dienst), welcher hauptsächlich für andere Prozesse verwendet wird. Ein Daemon sollte ohne 
Einfluss des Users laufen können.

## Erstellung eines Daemons

Um einen Daemon zu erstellen muss man zu erst ein Programm schreiben. In unserem Fall sollen wir das Programm in der Shell mit C programmieren. 
Mit ``` user@user-VirtualBox:~/mydaemon $ nano mydaemon.c ``` schreiben wir das C Programm in der Shell. 

```C
#include <stdio.h>
#include <stdlib.h>
#include <syslog.h>
#include <unistd.h>

int main () {
    openlog ("mydaemon", LOG_PID, LOG_DAEMON);

    syslog (LOG_NOTICE, "mydaemon started.");
    printf("Hello 1\n"); 
    fflush(stdout);
    sleep (2);
    
    printf("Hello 2\n"); 
    fflush(stdout);
    sleep (2);
    
    printf("Hello 3\n"); 
    fflush(stdout);
    sleep (2);
    
    syslog(LOG_WARNING, "bin bei der letzten Ausgabe...");
    printf("Hello 4\n"); 
    fflush(stdout);

    usleep(1000);
    syslog (LOG_NOTICE, "mydaemon terminated.");
    closelog();
    usleep(1000);

    return 0;
}
```
Dieses Beispielprogramm gibt vier mal "Hello" aus. Doch neben den normalen printfs schreibt dieses Programm auch einmal eine Warnung 
namens "bin bei der letzten Ausgabe..." und zwei Bemerkung "mydaemon started" "mydaemon terminated." in den Log. 

``` user@user-VirtualBox:~/mydaemon $ gcc -o mydaemon mydaemon.c ``` kompiliert dann das C Programm und ``` user@user-VirtualBox:~/mydaemon $ ./mydaemon ``` 
führt das Programm dann aus. Nach ein paar Sekunden sollte dann das hier ausgegeben werden.

```
user@user-VirtualBox:~/mydaemon $ ./mydaemon 
Hello 1
Hello 2
Hello 3
Hello 4
user@user-VirtualBox:~/mydaemon $ 
```
Wenn man danach ``` user@user-VirtualBox:~/mydaemon $ journalctl -u mydaemon ``` eingibt kann man folgendes im Log finden. 
```
Datum Uhrzeit user-VirtualBox mydaemon[53734]: mydaemon started
Datum Uhrzeit user-VirtualBox mydaemon[53734]: Hello 1
Datum Uhrzeit user-VirtualBox mydaemon[53734]: Hello 2
Datum Uhrzeit user-VirtualBox mydaemon[53734]: Hello 3
Datum Uhrzeit user-VirtualBox mydaemon[53734]: bin bei der letzten Ausgabe...
Datum Uhrzeit user-VirtualBox mydaemon[53734]: Hello 4
Datum Uhrzeit user-VirtualBox mydaemon[53734]: mydaemon terminated
```
```
user@user-VirtualBox:~/mydaemon $ journalctl -f
``` 
Lässt einen die noch reinkommenden Einträge live mit verfolgen
```
user@user-VirtualBox:~/mydaemon $ journalctl -f -p 4
```
Lässt einen die noch reinkommenden Einträge live mit verfolgen, priorisiert aber Warnungen.
```
user@user-VirtualBox:~/mydaemon $ journalctl -f -o verbose
```
Lässt einen die noch reinkommenden Einträge live mit verfolgen und gibt alle Details aus.
```
user@user-VirtualBox:~/mydaemon $ tail -f /var/log/syslog
```
Gibt anhängende Daten aus, wenn die Datei wächst.

## Erstellung eines Service
Um einen Service zu erstellen muss man zuerst via nano die mydaemon.service schreiben.
```
[Unit]
Description=my background program for testing system services

[Service]
ExecStart=/home/user/mydaemon/mydaemon
IgnoreSIGPIPE=false
KillMode=process
```
ExecStart ist er Befehl zum Starten des Programms. IgnoreSIGPIPE sagt ob die SIGPIPE ignoriert wird oder nicht. Der KillMode legt fest 
wie der Prozess getötet werden soll.

Danach muss man einen Link von unserer Service Datei in /etc/systemd/system erstelle. Dies geht wie folgt:
```
user@user-VirtualBox: ~/mydaemon$ sudo -i
root@user-VirtualBox: ~# cd /etc/systemd/system
root@user-VirtualBox: /etc/systemd/system# ln -s /home/user/mydaemon/mydaemon
```
Hiernach startet man den Dienst so:
```
user@user-VirtualBox: ~/mydaemon$ sudo systemctl start mydaemon
```
Mit journalctl -f kann man den Dienst auch wieder verfolgen.

## Daemon mit Autostart
Damit ein Daemon auch bei Systemstart automatisch ausgeführt wird muss man zuerst die Service Datei ein wenig verändern.
```
[Unit]
Description=my background program for testing system services

[Service]
ExecStart=/home/user/mydaemon/mydaemon
IgnoreSIGPIPE=false
KillMode=process

[Install]
WantedBy=multi-user.target
```
Dieser Zusatz besagt, dass der Dienst gestartet werden soll, sobald das System den Zustand Multi-User erreicht. 

Jetzt muss man den Daemon mit ``` user@user-VirtualBox: ~/mydaemon$ sudo systemctl enable mydaemon ``` aktivieren und danach das Gerät 
neu starten.
