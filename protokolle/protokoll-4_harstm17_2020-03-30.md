# Protokoll-4 LABOR/SX 3AHME (2019/20)

---------------------------------------------------------------------------------------------

* **Thema:** Dienste in Linux-Systemen
* **Datum:** 30.03.2020
* **Gefehlt:** -
* **Erstellt von:** Stefan Haring (harstm17)
* **Protokoll der letzten Einheit:** [Protokoll 3](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/edit/harstm17/protokolle/protokoll-3_harstm17_2020-03-23.md)

----------------------------------------------------------------------------------------------

## Inhaltsverzeichnis  

1. [Vorraussetzungen](#vorraussetzungen)
1. [Teil 1 Durcharbeiten der Unterlagen](#teil-1-durcharbeiten-der-unterlagen)
1. [Teil 2 Erstellung eines Dienstes](#teil-2-erstellung-eines-dienstes)
    * [Ablauf der Übung](#ablauf-der-übung)
    * [Beantwortung der Fragen](#beantwortung-der-fragen)
        * [Aufgabenstellung](#aufgabenstellung)
        * [C-Programm](#c-programm)
        * [Programm übersetzen](#programm-übersetzen)
        * [Programm testen](#programm-testen)

    
-------------------------------------------------------------------------------------------------------------------

### Vorraussetzungen

Vorraussetzend ist es, [die Linux Grundkenntnisse (e-Book LMS Bibliothek / Linux-1)](https://lms.at/mybib/MjM3NDc1ODU5/bibs/dotlrn_class_instance/xolrn__381036830.symlink/7BF1B31508DF3.symlink?resource_id=0-237477244-237484829-381037558-385942208&m=view#150874536) zu beherrschen und entweder eine Virtualbox installiert zu haben oder auf einem Ubuntu 18.04 System zu arbeiten. Ein funktionierender Internetzugang ist ebenso vorrausgesetzt.

-------------------------------------------------------------------------------------------------------------

### Teil 1 Durcharbeiten der Unterlagen

Hier gilt es [das LMS e-book Bibliothek / Linux-2 / Kapitel 1, 1.1, 1.3](https://lms.at/mybib/MjM3NDc1ODU5/bibs/dotlrn_class_instance/xolrn__381036830.symlink/9F2714A93B69A.symlink?resource_id=0-237477244-237484829-381037558-420357452&m=view#155470713) und [diese Internetseite](https://wiki.ubuntuusers.de/systemd/) durchzuarbeiten. Im Sinne von Durcharbeiten ist gemeint, das vollständige Verstehen des gelesenen Stoffes und das falls notwendige Nachrecherieren von nicht verstandenen Themen. 

-----------------------------------------------------------------------------------------------------------------

### Teil 2 Erstellung eines Dienstes
**(auch Dämon gennant)**

#### Ablauf der Übung

Normalerweise würde die Übung auf einem Raspberry PI mit Raspbian Lite System (ohne Desktop GUI)
stattfinden. Daher sollte auf IDE, Nautilus etc. verzichtet werden. Nur eine (oder mehrere) Shell(s) öffnen
und darin mit Shell-Kommandos und Text-Editor nano arbeiten.

Beim Folgen des [Links](https://lms.at/mybib/MjM3NDc1ODU5/bibs/dotlrn_class_instance/xolrn__381036830.symlink/9F2714A93B69A.symlink?resource_id=0-237477244-237484829-381037558-420357452&m=view#155470740) stößt man auf eine Aufgabenstellung, mit der man mit Hilfe der Programmiersprache C einen Dienst erstellt.

#### Beantwortung der Fragen

1. Was bedeutet der Begriff Dämon in Linux-Systemen und in Java?

Selbstinterpretation:
>Ein Dämon ist ein Hintergrundprogramm, welches bestimmte Dienste zur Verfügung stellt.<

[Wikipedia](https://de.wikipedia.org/wiki/Daemon) zitiert folgendes:
>Als Daemon [ˈdiːmən] oder Dämon (auch häufig in der Schreibweise Demon) bezeichnet man unter Unix oder unixartigen Systemen ein Programm, das im Hintergrund abläuft und bestimmte Dienste zur Verfügung stellt. Benutzerinteraktionen finden hierbei nur auf indirektem Weg statt, zum Beispiel über Signale, Pipes und vor allem (Netzwerk-)Sockets. Der Begriff Daemon wird auch als Abkürzung von disk and execution monitor interpretiert, was jedoch ein Backronym ist.<

2. Die Übung 1 wie im e-Book beschrieben durchführen

##### Aufgabenstellung

Mit dem folgenden C-Programm kann man auf zB. einem Raspberry Pi (Jessi) einen Dienst erstellen. Der Dienst hat die Aufgabe 4x Text im Abstand von 2 Sekunden ins Log schreiben. Dies geschieht gewöhnlich für einen Dienst im Hintergrund.

##### C Programm

Die klassische Vorgangsweise bestand darin in einem Programm mittels fork() einen Kindprozess abzuspalten, und diesen dann im Hintergrund weiterlaufen zu lassen. Mit systemd ist das nicht mehr erforderlich. Es wird lediglich ein C-Programm benötigt, das die gewünschte Aufgabe erfüllt.

Datei *mydaemon.c*
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
Dieses C-Programm musste in unserem Fall auf der Virtual-box gespeichert werden. Das Dateiende sollte ***.c*** lauten. Ich habe das Programm zuerst unter dem Dateiende ***.txt*** gespeichert gehabt. Dies führte später zu Komplikationen, wie bald folgt.

##### Programm übersetzen

In diesem Punkt übersetzen wir das vorgefertigte C-Programm mit dem GNU GCC Compiler. Folgende Befehle wurden dabei angewandt (Grafik ist eine Bildschirmaufnahme):
![](https://cdn.discordapp.com/attachments/692288920716705812/694187716388323358/shell1.PNG)

Man bemerkt, dass manche Befehle öfters ausgeführt worden sind. Grund waren eben die obenbeschriebenen Komplikationen mit dem Dateiende.
**Das fertige Programm *mydaemon* steht nun bereit, um als Dienst im Hintergrund gestartet zu werden.**

##### Programm testen

Das Programm wurde mit Hilfe des folgenden Befehls gestartet.
```./mydaemon```
Mit diesem Befehl kann man testen ob das Programm funktioniert. In der Shell schaut das dann wie folgt aus:
```
user@pi:~/mydaemon $ ./mydaemon 
Hello 1
Hello 2
Hello 3
Hello4
user@pi:~/mydaemon $ 
```
Dieser Befehl wurde auch schon in der obigen Bildschirmaufnahme ausgeführt.
Danach kann man in weiteren Shells parallel dazu die Ausgabe im Log und journald anzeigen lassen:
*(Befehl folgt immer nach dem Dollar-Zeichen ($))*
```
user@pi:~/mydaemon $ journalctl -f
```
```
user@pi:~/mydaemon $ journalctl -f -p 4
```
```
user@pi:~/mydaemon $ journalctl -f -v verbose
```
```
user@pi:~/mydaemon $ tail -f /var/log/syslog
```


Folgende Bildschirmaufnahmen veranschaulichen den 1. und den 4. der ausgeführten Befehle grafisch:

![](https://media.discordapp.net/attachments/692288920716705812/694214053471715328/shell2.PNG?width=1023&height=216)

![](https://media.discordapp.net/attachments/692288920716705812/694214039974182963/shell4.PNG?width=1023&height=232)
