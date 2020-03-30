# Protokoll LA2/SX 3AHME (2019/20)

* **Thema:** Erstellung eines Dienstes (Dämon) und  Endlos-Dienst automatisch starten
* **Datum:** 30.03.2020
* **Erstellt von:** Felix Hamrle
* **Protokoll nächste Einheit:** --

## Inhaltsverzeichnis

1. [Was bedeutet der Begriff Dämon in Linux-Systemen und in Java?](#was-bedeutet-der-begriff-dämon-in-linux-systemen-und-in-java)    
   1. [Linux](#linux)  
   2. [Java](#java)  
2. [Einen Dämon erstellen](#einen-dämon-erstellen)   
3. [Service erstellen](#service-erstellen)  
2. [Endlos-Dienst automatisch starten](#endlos-dienst-automatisch-starten)  




## Was bedeutet der Begriff Dämon in Linux-Systemen und in Java?

### Linux

Auf ziemlich allen Systemen lauft das Programm rsyslogd im Hintergrund. Dieses  
Programm stellt einen Logging-Dinst zur Verfügung. Solche Hintergrundprogramme  
werden Dämon genant. 

### Java

In Java ist es der Daemon Thread, ein Service-Provider-Thread, welcher Dienste  
für den Benutzer-Thread in unterstützenden Aufgaben im Hintergrund bereitstellt.  
Dieser Daemon Thread ist ein Thread mit niedriger Priorität.

## Einen Dämon erstellen

Um einen eigenen Dämon zu erstellen erstellt man in der Konsole in irgendeinem Verzeichnis 
mit `mkdir mydeamon` ein neues Verzeichnis. Dann wechselt man mit `cd mydeamon` in dieses  
Verzeichnis. Mit `touch mydeamon.c` erstellt man eine C-Datei und mit `nano mydeamon.c` kann  
man diese Datei dann bearbeiten. In diese C-Datei schreibt man dieses C-Programm:

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
Mit `gcc -o mydeamon mydeamon.c` compiliert man es. Dann kann man es mit `./mydeamon` ausführen.
Die Ausgabe vom Terminal sollte dann so ausschauen:

```console
felix@felix-VirtualBox:~/Schreibtisch/mydeamon$ ./mydeamon 
Hello 1
Hello 2
Hello 3
Hello 4
```
Dies kann man `journalctl` überprüfen. Um die neuesten Einträge im Journal gibt man  
nach `journalctl` `-f` ein. Um nach die Ausgabe nach Message-Prioritäten zu Filtern gibt man nach `journalctl` `-p`  
und dann eine Zahl zwischen 0 - 7 (0 Emergencies, 7 debug) um nur warnings auszugeben schreibt man nach  
`journalctl` `-p` einfach einen 4 (`journalctl -p 4`). Weitere Informationen findet man über `man journalctl`.

## Service erstellen

Als erster um einen Service zu erstellen müssen wir die Service-Datei `mydaemon.service` erstellen. In diese Schreiben  
wir dann mit `nano mydaemon.service` dort schreibt man dann:

```console
[Unit]
Description=my background program for testing system services

[Service]
ExecStart=PfadZuMyDeamon/mydaemon
IgnoreSIGPIPE=false
KillMode=process
```

Wobei **KillMode** gibt an wie die Prozesse dieses Programmes abgeschaltet  werden soll und **IgnoreSIGPIPE** bewirkt das  
**SIGPIPE** im ausgeführten Prozess ignoriert wird. **IgnoreSIGPIPE** kann true oder false sein. In den meisten fällen  
ist es true also ignoriert es **SIGPIPE** im ausgeführten Prozess. **SIGPIPE** ist wenn auf ein pipe ohnen Empfänger  
geschrieben wird. Eine pipe ist ein Datenstrom zwischen zwei Prozessen.  
**ExecStart** gibt den Pfad des auszuführenden Programmes.  
  
Jetzt müssen wir in /etc/systemd/system einen Link auf mydaemon.service. Dafür muss man als erstes der Superuser  
werden das geht mit `sudo -i` dort muss man dann ein Passwort eingeben. Danach müssen wir zum Verzeichnis  
system wechsel das geht mit `cd /etc/systemd/system` dort erstellt man dann mit `ln -s /home/user/mydaemon/mydaemon`  
einen Link zu mydaemon.service. Und mit `exit` kommt dann wieder aus dem Superuser raus.


## Endlos-Dienst automatisch starten

Dienste sollten beim Systemstart automatisch zum richtigen Zeitpunkt gestartet werden.  
Das geht mit `sudo systemctl enable mydaemon` aber dann erscheint eine Fehlermeldung. Dies lässt sich ganz einfach  
beheben. Man muss in der Service-Datei mydaemon.service noch einen Zusätzlichen Eintrag machen. Im ganzen sollte  
es dann so ausschauen:

```console
[Unit]
Description=my background program for testing system services

[Service]
ExecStart=PfadZuMyDeamon/mydaemon
IgnoreSIGPIPE=false
KillMode=process

[Install]
WantedBy=multi-user.target
```

Damit es ein Endlos-Dienst ist soll man das Programm in mydaemon.c so ändern:

```C
#include <stdio.h>
#include <stdlib.h>
#include <syslog.h>
#include <unistd.h>

int main () {

    while
    {
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
```

Das sollte man dann statt dem was in mydaemon.c steht mit dem oben stehenden ersetzen und natürlich dann mit  
`gcc -o mydeamon mydeamon.c` neu compiliert.

Um dann mit sudo reboot das System neu starten. Mit `journalctl -f` sieht man, dass das Programm nun  
in einer Endlosschleife ausgeführt wird.
