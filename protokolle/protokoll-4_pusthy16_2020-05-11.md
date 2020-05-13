# 4. Protokoll
---------------------------------------------
## Thema: Dienste in Linux
---------------------------------------------
* Datum:      11.05.2020
* Gruppe:     3  
* Abwesend:   keiner
* Verfasser:  Thomas Pust 
* Klasse:     3AHME
* Schuljahr:  2019/20
---------------------------------------------
## Inhaltsverzeichnis
* [Voraussetzungen](#voraussetzungen)
  * [Grundlagen](#grundlagen)
* [Erstellung eines Dienstes](#erstellung-eines-dienstes)
  * [Übung](#übung)
  * [Wichtige Begriffe](#wichtige-begriffe)
* [Endlos-Dienst automatisch starten lassen](#endlos-dienst-automatisch-starten-lassen)


---------------------------------------------
### Voraussetzungen
Um an dieser Übung teilnehmen zu dürfen benötigt man:
* Linux Grundkenntnisse 
* Ubuntu 18.04 System native oder via Virtualisierung (zB Virtualbox)

#### Grundlagen
Zuerst mussten wir 2 Skripten durcharbeiten, um an das nötige Know-How für die Übung zu kommen:

-> Erstes Skriptum: Klicken Sie [hier](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#155470713 ).

-> Zweites Skriptum: Klicken sie [hier](https://wiki.ubuntuusers.de/systemd/)

### Erstellung eines Dienstes
Ein Dämon ist ein Programm, das im Hintergrund abläuft und bestimmte Dienste zur Verfügung stellt, welches auf einem Unix bzw ein unixartiges Systemen läuft.

#### Übung
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
thomas@thomas-VirtualBox:~$ mkdir mydaemon                <--- neuen Ornder erstellen
thomas@thomas-VirtualBox:~$ cd mydaemon                   <--- in den Ordner reingehen
thomas@thomas-VirtualBox:~$ nano mydaemon.c               <--- Terminal Texteditor öffen und C Programm einfügen
thomas@thomas-VirtualBox:~$ gcc -o mydaemon mydaemon.c    <--- Übersetzten mit GCC Compiler
thomas@thomas-VirtualBox:~$ ls -l  
```
Nano Kommandos: STRG + O zum Speichern udn mit STRG + X verlassen

Nun haben wir einen neuen Ornder angelegt mit einer main.c Datei. Diese können wir mit dem Befehl ```./mydaemon``` ausführen.  
Das ausgeführte Programm sieht dann so aus:

![](https://cdn.discordapp.com/attachments/692432976503373854/694930441769320496/Bild1.png)


Als Nächstes testen wir unser Programm. Wir können man mit Hilfe von weiteren Shells mit folgenden Befehelen die Ausgabe im Log oder im journald anzeigen lassen.
```
thomas@thomas-VirtualBox:~$ journalctl -f
thomas@thomas-VirtualBox:~$ journalctl -f -p 4
thomas@thomas-VirtualBox:~$ journalctl -f -v verbose
thomas@thomas-VirtualBox:~$ tail -f /var/log/syslog
```
Danach muss man eine neue Datei erstellen namens "mydaemon.service".
Wenn man diese erstellt hat muss man als Super User einsteigen.

Beim Erstellen von mydaemon.service an sich hatte ich keine Probleme nur konnte hat es nicht geklappt den Link auf die Service Datei zu erstellen.

Leider bin ich nicht weiter als hierhin gekommen.

Weiter Schritte wären, den Service starten, stoppen und beobachten. Außerdem ebenso einen Autostart für diesen Dienst zu errichten.

#### Wichtige Begriffe
Theorie:
* ExecStart: ExecStart ist der Befehl, der beim Start der Unit ausgeführt wird.

* Ignore SIGPIPE: Wird beim Versuch verschickt, in eine nicht mehr existierende Pipe zu schreiben. (Pipe - "Datenstrom" zwischen zwei Programme)

* KillMode: Legt fest, wie die Prozesse dieser Unit beendet werden soll bzw getötet werden soll. Entweder mit **control-group**, **process**, **mixed** oder **none**.

### Endlos-Dienst automatisch starten lassen
Zu diesem Punkt bin ich in der regulären Zeit des Unterrichts nicht gekommen.
