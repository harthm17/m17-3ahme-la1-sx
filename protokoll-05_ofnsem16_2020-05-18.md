# 5. Protokoll
------------------------------------
## Thema: Installationspakete
------------------------------------
* Datum:      18.05.2020
* Gruppe:     3
* Abwesend:   keiner
* Verfasser:  Ofner Sebastian
* Klasse:     3AHME/AHME17
* Schuljahr:  2019/20
------------------------------------
## Inhaltsverzeichnis
* [tar.gz-Datei](#targz-datei)
* [Theorie](#theorie)
* [Erstellung einer Java GUI](#erstellung-einer-java-gui)
* [Übung 1](#übung-1)
------------------------------------
### tar.gz-Datei
Herr Professor Steiner zeigte uns nochmals an einem Beispiel wie man eine **tar.gz-Datei** erstellt. Weitere Informationen zur tar.gz finden Sie [Hier](https://wiki.ubuntuusers.de/tar/)

Mit diesem Befehl lässt sich eine tar.gz-Datei über die Konsole erstellen:
```
tar Optionen Datei
```
Optionen können Sie im [oberen Link](https://wiki.ubuntuusers.de/tar/) nachlesen.

### Theorie
Als Erstes mussten wir in unserem E-Book **Linux 2** uns **Kapitel 3 und 3.1** durchlesen.

[Hier zum E-Book](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#473229838)

### Erstellung einer Java GUI
Als nächstes mussten wir eine Java GUI mit Netbeams erstellen, wie das funktioniert wird in [diesem Video](https://cloud.htl-mechatronik.at/index.php/s/AlyXs7YglQDLZSP)
erklärt, einfach Schritt für Schritt den Anweisungen folgen.

### Übung 1
Wir sollten die Übung 1 aus dem selben [E-Book (Linux 2)](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#473229838)
ab arbeiten.

#### Schritt 1: Java Programm erstellen
Schritt 1 wurde von uns schon mit Hilfe des Videos aus dem vorherigen Punkt erledigt.

#### Schritt 2: Debian Paketverzeichnis erstellen
Als Erstes mussten wir einen Unterordner für ein Debianpaket erstellen.
Dafür müssen folgende Befehle in die Konsole eingegeben werden:
```
user@host:~$ mkdir sx-guiapp_1.0~1_all      <--- erstellung Ordner
user@host:~$ cd sx-guiapp_1.0~1_all         <--- gehe zum Ordner
user@host:~/sx-guiapp_1.0~1_all$ 
```

#### Schritt 3: Datei DEBIAN/control
Es muss ein Unterordner **Debian** erstellt werden mit der Datei **control**. 
Dafür müssen folgende Befehle in die Konsole eingegeben werden:
```
user@host:~/sx-guiapp_1.0~1_all$ mkdir DEBIAN
user@host:~/sx-guiapp_1.0~1_all$ cd DEBIAN
user@host:~/sx-guiapp_1.0~1_all/DEBIAN$ nano control
```

In die Datei **control** muss folgendes geschrieben werden:
```
Package: sx-guiapp
Architecture: all
Depends: default-jre (>=2:1.11)
Installed-Size: 1000
Maintainer: Manfred Steiner <sx@htl-kaindorf.ac.at>
Description: My first Java GUI Application
```

Es fehlt noch eine Zeile, die man mit Hilfe [dieser Seite](https://www.debian.org/doc/debian-policy/ch-controlfields.html) finden
sollte, bin damit aber nicht fertig geworden.
