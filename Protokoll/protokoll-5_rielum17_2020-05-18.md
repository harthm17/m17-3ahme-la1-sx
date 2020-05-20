# Protokoll-5 LABOR/SX 3AHME (2019/20)

---------------------------------------------------------------------------------------------

* **Thema:** Linux Grundkenntnisse 2
* **Datum:** 18.05.2020
* **Gefehlt:** -
* **Erstellt von:** Riegelnegg Lukas (rielum17)
* **Protokoll der letzten Einheit:** [Protokoll 4](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/rielum17/Protokoll/protokoll-4_rielum17_2020-05-11.md)
----------------------------------------------------------------------------------------------

* [Dämon](#Dämon)
  * [Übung](#Erstellen eines Dämons)
* [Endlos-Dienst automatisch starten lassen](#endlos-dienst-automatisch-starten-lassen)

----------------------------------------------------------------------------------------------------------

### Dämon
Ein Dämon ist ein Programm, das im Hintergrund abläuft und bestimmte Dienste zur Verfügung stellt, welches auf einem Unix bzw ein unixartiges Systemen läuft.

#### Erstellen eines Dämons
In dieser Übung sollen wir einen Dienst erstellen, welcher ein C-Programm laufen lässt. Dieses Programm wird im Hintergrund laufen und gibt viermal einen Text aus und zwar alle 2 Sekunden.

Der erste Schritt ist es, dass C Programm zu erstellen bzw eine main.c Datei.

Quellcode:
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

Danach übersetzten wir das C-Programm in unserem Terminal. Hierbei erstellen wir einen neuen Ordner und eine neue main Datei, wobei die Erstellung der neuen main Datei nicht unbedingt notwendig ist.  
Wir haben folgende Befehle verwendet, mit den Pfeilen wurden die einzelnen Schirtte nochmals genauer erklärt:
(Bei dieser Übung sind bei in der Einheit Probleme aufgetreten, konnte diese aber im nachhinein lösen)
```
rico@ra-s-m005:~$ mkdir mydaemon                <--- neuen Ornder erstellen
rico@ra-s-m005:~$ cd mydaemon                   <--- in den Ordner reingehen
rico@ra-s-m005:~$ nano mydaemon.c               <--- Terminal Texteditor öffen und C Programm einfügen
rico@ra-s-m005:~$ gcc -o mydaemon mydaemon.c    <--- Übersetzten mit GCC Compiler
rico@ra-s-m005:~$ ls -l  
```
Nano Kommandos: STRG + O zum Speichern udn mit STRG + X verlassen

Nun haben wir einen neuen Ornder angelegt mit einer main.c Datei. Diese können wir mit dem Befehl ```./mydaemon``` ausführen.  
Das ausgeführte Programm sieht dann so aus:

![](file:///home/rico/Schreibtisch/Home%20office/Lab/SX/Bildschirmfoto_2020-05-20_12-02-43.png)

Als Nächstes testen wir unser Programm. Wir können man mit Hilfe von weiteren Shells mit folgenden Befehelen die Ausgabe im Log oder im journald anzeigen lassen.
```
rico@ra-s-m005:~$ journalctl -f
rico@ra-s-m005:~$ journalctl -f -p 4
rico@ra-s-m005:~$ journalctl -f -v verbose
rico@ra-s-m005:~$ tail -f /var/log/syslog
```
Danach muss man eine neue Datei erstellen Namens "mydaemon.service".
Wenn man diese erstellt hat muss man als Super User einsteigen.

### Endlos-Dienst automatisch starten lassen
Möchte man seinen Daemon per Autostart ausführen lassen, geht das so:

Der Befehl dafür lautet `sudo systemctl enable mydaemon`. Doch dies alleine führt bloß zu einer Fehlermeldung. Durch das Einfügen von
```
[Install]
WantedBy=multi-user.target
```
 in die Datei mydaemon.service wird vermittelt, dass mydaemon beim Eintritt in Phase der Multi-User-Fähigkeit gestartet werden soll. Mit dieser getroffenen Maßnahme kann mydaemon nun mit dem obigen Befehl in den Autostart eingegliedert werden. Startet man den Rechner neu (dies geht aus der Shell mit `reboot` oder `sudo reboot`), kann die Ausführung von mydaemon überprüft werden.
