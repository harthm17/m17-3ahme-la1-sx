# Protokoll LAB/Sx 3.AHME (2020)

* **Thema:** Erstellung eines Dienstes (Dämon) 
* **Datum:** 30.03.2020
* **Gefehlt:** -
* **Esrtellt von:** Franz Lieleg (liefrm)
* **Protokoll der letzten Einheit:**![3tes Protokol](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/liefrm17/SxLab%20Protokolle/protokoll-3_liefrm_2020-3-25.md)
* **Protokoll der nächsten Einheit:**

------------------------------------------------------------------------------------------------------------------------
## Inhaltsverzeichnis 

1) [Vorausgesetzte Fähigkeiten](#vorausgesetzte-fähigkeiten)
1) [Durcharbeiten der neuen Unterlagen](#durcharbeiten-der-neuen-unterlagen)
1) [Was ist Dämon?](#was-ist-dämon)
1) [Übung 1: Erstellen eines Dienstes](#übung-1-erstellen-eines-dienstes)
   * [Aufgabenstellung](#aufgabenstellung)
   * [C-Programm](#c-programm)
   * [Programm übersetzen](#programm-übersetzen)
   * [Programm testen](#programm-testen)
1) [Resümee](#resümee)

------------------------------------------------------------------------------------------------------------------------------
## Vorausgesetzte Fähigkeiten

Für diese Aufgabe sollte/müssen gewisse Vorkentnisse vorhanden sein, denn sonst wird sie um einiges schwieriger.
Voraussetzungen für diese Übung sind: 
 * Gewisse Vorkenntnisse, nachzulesen auf LMS im E-Book [Linux-Teil 1](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/7BF1B31508DF3.symlink?resource_id=0-385942208&m=view#154334970), Laborkurs Sx
 * Zugriff auf ein Ubuntu 18.04 System (bereits in der letzten Einheit installiert)
 
Link (Eigenes Protokoll) zum Einrichten eines Ubuntu 18.04 Systemes:[Installation von Ubuntu 18.04 LTS + virtuelle Maschine]https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/liefrm17/SxLab%20Protokolle/protokoll-3_liefrm_2020-3-25.md

------------------------------------------------------------------------------------------------------------------------------------
## Durcharbeiten der neuen Unterlagen

Diese Unterlagen beinhalten die Voraussetzungen für diese Übung.

**Auftrag:** 
  * Selbstendiges durcharbeiten des folgenden Dokumentes: [LMS/LAB Sx/E-Book Linux-Teil 2/Kapitel 1.,1.1,1.3](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#155470713)
  * Recherche auch im Internet möglich: https://wiki.ubuntuusers.de/systemd/
  
---------------------------------------------------------------------------------------------------------------------------------------
## Was ist Dämon?

Der Begriff Dämon beschreibt einen Dienst/Programm, der im Hintergrund läuft. Es stellt diverse Dienste zur Verfügung

Genauere und ausführlichere Definition: [Wikipedia](https://de.wikipedia.org/wiki/Daemon)

>Als Daemon [ˈdiːmən] oder Dämon (auch häufig in der Schreibweise Demon) bezeichnet man unter Unix oder unixartigen Systemen ein Programm, das im Hintergrund abläuft und bestimmte Dienste zur Verfügung stellt. Benutzerinteraktionen finden hierbei nur auf indirektem Weg statt, zum Beispiel über Signale, Pipes und vor allem (Netzwerk-)Sockets. Der Begriff Daemon wird auch als Abkürzung von disk and execution monitor interpretiert, was jedoch ein Backronym ist.

----------------------------------------------------------------------------------------------------------------------------------------
## Übung 1: Erstellen eines Dienstes

### Aufgabenstellung

Es soll auf einem Raspberry PI (jessi) mit Hilfe eines C-Programmes ein Dienst erstellt werden. Dieser soll, während er im Hintergrund läuft, einen Text im 2 Sekundenabstand viermal hintereinander im Log ausgeben. 

**Die Folgenden Arbeiten werden ausschließlich im Terminal abgewickelt!!!**

### C-Programm

Folgendes **C-Programm** ist gegeben:

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
### Programm übersetzen

***Hinweis:*** Alle hier im Protokoll angeführten Befehle sind im Terminal einzugeben!

Zuerst wird als User im Home Verzeichnis ein Arbeitsverzeichnis (mydaemon) erstellt, darin wird die Datei mydaemon angelegt. Anschließend wird der Quelltext übersetzt.

**Benötigte Befehle:**

```
user@pi:~$ mkdir mydaemon
user@pi:~# cd mydaemon
user@pi:~/mydaemon $ nano mydaemon.c
...
user@pi:~/mydaemon $ gcc -o mydaemon mydaemon.c
user@pi:~/mydaemon $ ls -l
insgesamt 12
-rwxr-xr-x 1 franz franz 8592 Apr 1 17:00 mydaemon
-rw-r--r-- 1 franz franz  575 Apr 1 17:00 mydaemon.c
```

So sieht das Terminal nach erfolgreichem ausführen der erwähnten Befehle dann aus:

![](https://media.discordapp.net/attachments/691664570208616518/695325691142733875/unknown.png)

**Achtung:** Diese Auffnahme unterscheidet sich, zu sehen am ersten Befehl, geringfügig verglichen zu den Befehlen die vorhin angeführt wurden! Grund dafür ist, das diese Datei bereits exestiert.

***Hinweis:*** 

* Die Kenntnisse zu den Befehlen sollten schon vorhanden sein, deswegen werden sie hier nicht mehr angeführt. Wenn sie vergessen    wurden, dann bitte unter [Linux-Teil 1](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/7BF1B31508DF3.symlink?resource_id=0-385942208&m=view#154334970) wieder auffrischen.
    
* Das vorhin angeführte C-Programm wird korrekt im Texteditor **nano** eingetippt.

## Programm testen

Das Programm wird danach mit dem Befehl ```./mydaemon``` in der Shell gestartet gestartet!

So sieht das Terminal nach dem erfolgreichen ausführen des erwähnten Befehles dann aus:

![](https://cdn.discordapp.com/attachments/691664570208616518/695327860205944832/unknown.png)

In weiteren geöffneten Shells kann man die Ausgabe im Log und im journald parallel dazu anzeigen lassen.

**Folgende Befehle dazu:**
```
user@pi:~/mydaemon $ journalctl -f
user@pi:~/mydaemon $ journalctl -f -p 4
user@pi:~/mydaemon $ journalctl -f -v verbose
user@pi:~/mydaemon $ tail -f /var/log/syslog
```
------------------------------------------------------------------------------------------------------------------------------
## Resümee
Das Ausführen der Aufgabe hat sich als schwerer entpuppt als ich erwatet hätte. Das genaue Arbeiten und das Verstehen des Stoffes empfand ich mühevoll. Ich habe mir mehrmals Hilfe bei meinen Schulkollegen gesucht, dennoch kam ich nur beschwerlich voran. Dadurch schon alleine das Durcharbeiten des Skriptes eine gewisse Zeit in Anspruch genommen hatte, man siehe es am Protokoll, kam ich nicht schnell genung voran, um die andere Aufgabenstellungen erfüllen zu können.
