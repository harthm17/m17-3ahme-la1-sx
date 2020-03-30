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

* [Grundlegendes](#grundlegendes)
* [Erstellung eines Dienstes](#erstellung-eines-dienstes)
* [Endlos-Dienst automatisch starten lassen](#endlos-dienst-automatisch-starten-lassen)

---------------------------------------------
### Grundlegendes
Voraussetzungen...
Unterlagen...

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

