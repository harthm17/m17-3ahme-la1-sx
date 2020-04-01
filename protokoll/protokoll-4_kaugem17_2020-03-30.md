# 4. Protokoll

-------------------------------------------------

## Thema: Dienste in Linux Systemen

-------------------------------------------------

Übungsdatum:   Montag, 30.03.2020     
Übungszeit:    14:10 bis 16:30      
Übungsort:     St. Veit in der Südsteiermark, Home-Office    
Verfasser:     Georg Kaufmann    
Abwesend:      keiner      
Anwesend:      Felix Hamrle, Stefan Haring, Thomas Harrer, Georg Kaufmann, Andreas Kogler, Franz Lieleg, Simon Marcher

-------------------------------------------------

### Inhaltsverzeichnis
1) [Voraussetzungen](#voraussetzungen)
1) [Teil 1](#teil-1) 
1) [Teil 2](#teil-2) 
   * [Begriff Dämon](#begriff-dämon)
   * [Übung 1](#übung-1)
      * [Aufgabenstellung](#aufgabenstellung)
      * [Übersetzen des Programms](#übersetzen-des-programms)
      * [Testen des Programms](#testen-des-programms)
1) [Resümee](#resümee)

-------------------------------------------------

### Voraussetzungen
Um die folgenden Aufgaben der Laboreinheit durchführen zu können muss man folgende Voraussetzungen mit sich bringen. Man sollte Linux Grundkentnisse, E-Book Linux-1, haben und ein Ubuntu 18.04 System zur Verfügung haben.      
Wie man ein solches als Virtualbox installieren kann sieht man im folgendem [Protkoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/kaugem17/protokoll/protokoll-3_kaugem17_2020-03-23.md).

-------------------------------------------------

### Teil 1
Teil 1 der Angabe war das durchlesen des E-Books Linux-2, Kapitel 1, 1.1, 1.3 und das durchlesesen folgender [Seite](https://wiki.ubuntuusers.de/systemd/). Dies ist in der LMS Bibliothek LA1SX verfügbar. 

-------------------------------------------------

### Teil 2
#### Begriff Dämon
Der Begriff Dämon beschreibt einen Prozess unter Linux/Java der im Hintergrund läuft und nicht direkt interagiert wird. Dieser stellt verschiedene Dienste zur Verfügung.

#### Übung 1
##### Aufgabenstellung
In der folgenden Übung soll man einen Dienst, für einen Raspberry PI (Jessi) mit Hilfe von einem C-Programm erstellen. Dieser Dienst gibt viermal einen Text im Abstand von zwei Sekunden im Hintergrund aus. 

##### C-Programm
Im folgenden ist das gegebene C-Programm. 

``` C  

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

##### Übersetzen des Programms
Folgende Befehle werden dazu in der Shell verwendet. 
| Befehl |  |
| ------ | ------ |
| ```mkdir mydaemon``` | Verzeichniss mydeamon erstellen |
| ```cd mydaemon``` | in das Verzeichniss mydeamon wechseln |
| ```nano mydaemon.c``` | C-Programm als Datei mydeamon.c in diesem Verzeichniss anlegen |
| ```gcc -o mydaemon mydaemon.c``` | Übersetzen des Programms mit dem GNU Compiler |
| ```ls -l```| Listing der Infos zu diesem Programm |
    
![Bild](https://cdn.discordapp.com/attachments/692288920716705812/694963017523134584/Konsole12.png)
    
##### Testen des Programms
Folgender Befehl wird dazu in der Shell verwendet.
| Befehl |  |
| ------ | ------ |
| ```./mydaemon``` | Ausführen des Programms |    

Die Ausgabe beinhaltet vier mal das Wort Hello mit einer jeweiligen Nummer.
    
![Bild](https://cdn.discordapp.com/attachments/692288920716705812/694961627283324989/Konsole2.png)    
    
Mit folgenden Befehlen kann man die Ausgabe im Log und journald in anderen Shells parallel anzeigen lassen.     
    
```journalctl -f```   
```journalctl -f -p 4```    
```journalctl -f -v verbose```    
```tail -f /var/log/syslog```   

-------------------------------------------------

### Resümee
Leider habe ich nicht mehr geschafft. Ein Grund dafür war das genaue durchlesen des gegebenen Skriptes. 
