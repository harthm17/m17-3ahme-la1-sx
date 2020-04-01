# 4. Protokoll
---------------------------------------------
## Thema: Dienste in Linux Systemen
---------------------------------------------
* Datum:      30.03.2020
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
* [Endlos-Dienst automatisch starten lassen](#endlos-dienst-automatisch-starten-lassen)


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


Punkt 2 Übung

Punkt 3 genauer erklären


ExecStart:

IgnoreSIGPIPE:

KillMode:

### Endlos-Dienst automatisch starten lassen
Zu diesem Punkt bin ich in der regulären Zeit des Unterrichts nicht gekommen.
