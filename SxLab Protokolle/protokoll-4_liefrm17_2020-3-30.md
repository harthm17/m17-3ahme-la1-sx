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
  * [Übersetzen](#übersetzen)

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

Der Begriff Dämon beschreibt einen Dienst/Programm, dass im Hintergrund läuft. Es stellt diverse Dienste zur Verfügung

Genauere und ausführlichere Definition: [Wikipedia](https://de.wikipedia.org/wiki/Daemon)

>Als Daemon [ˈdiːmən] oder Dämon (auch häufig in der Schreibweise Demon) bezeichnet man unter Unix oder unixartigen Systemen ein Programm, das im Hintergrund abläuft und bestimmte Dienste zur Verfügung stellt. Benutzerinteraktionen finden hierbei nur auf indirektem Weg statt, zum Beispiel über Signale, Pipes und vor allem (Netzwerk-)Sockets. Der Begriff Daemon wird auch als Abkürzung von disk and execution monitor interpretiert, was jedoch ein Backronym ist.

----------------------------------------------------------------------------------------------------------------------------------------
## Übung 1: Erstellen eines Dienstes

## Aufgabenstellung

Es soll auf einem Raspberry PI (jessi) mit Hilfe eines C-Programmes ein Dienst erstellt werden. Dieser soll, während er im Hintergrund läuft, einen Text im 2 Sekundenabstand viermal hintereinander ausgeben. 

Das ganze geschiet in unserem Fall nur im Terminal.

## C-Programm

Folgendes **C-Programm** ist gegeben:

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


  
