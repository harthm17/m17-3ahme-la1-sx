# 6. Protokoll
---------------------------------------------
## Thema: Debian Paket erzeugen
---------------------------------------------
* Datum:      27.04.2020
* Gruppe:     2  
* Abwesend:   keiner
* Verfasser:  Thomas Harrer 
* Klasse:     3AHME
* Schuljahr:  2019/20
---------------------------------------------
## Inhaltsverzeichnis
* [Voraussetzungen](#voraussetzungen)
* [Übung zur Erstellung eines Debian Paketes](#übung-zur-erstellung-eines-debian-paketes)
* [Feedback](#feedback)

---------------------------------------------
## Voraussetungen
Unser erster Arbeitsauftrag war folgende Kapitel im Linux 2 Skriptum durchzulesen.
* [Kapitel 3](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#472857424)
* [Kapitel 3.1](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#472937916)

In diesen Kapiteln wurden viele Grundlegende Sachen erklärt, wie Installationpakete, Tools und Konfigurationdatein.

Dannach mussten wir die zum [Kapitel 3.2](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#473068402) erledigen.

Um zu den jeweiligen Kapiteln zu kommen, klicken Sie einfach drauf.

## Übung zur Erstellung eines Debian Paketes
### Schritt 1 - Erstellung eines Java Programms
Folgende Schritte sind zu befolgen:
1) Anlegen eines neuen Java Projekts. In meinem Fall hieß das Projekt "harthm17".
2) Dann legen wir ein neues Package an.
3) Dannach erstelen wir eine neue JFrame erzeugen.
4) Dannach müssen wir Mindestgröße konfigurieren, Fenster in der Bildschirmmitte öffnen lassen.
5) Dann müssen wir einen "Flow Layout" setzen.
6) Der nächste Schritt ist es einen "Press Button" einfügen.
7) In der Button-Handler-Methode ein Dialogfenster öffnen und einen Text ausgegeben.
8) Dannach müssen wir das Programm ausführen und testen.
9) Das Programm muss noch mit "Build and Clean" übersetzt,
10) In dem dist Ordner ist die fertige Java Datei zum entnehmen bereit.

Falls dabei Probleme auftreten, können Sie diese Video anschauen.
In diesm Video wird alles nochmals ausführlich erklärt.
Um zum Video zu gelangen, klicken Sie [hier](https://cloud.htl-mechatronik.at/index.php/s/AlyXs7YglQDLZSP).

### Schritt 2 - Debian Paketverzeichnis erstellen
Nun erstellen wir einen neuen Ordner für das Debianpaket.
```
thomas@thomas-VirtualBox:~$ mkdir harthm17-guiapp_1.0~1_all
thomas@thomas-VirtualBox:~$ cd harthm17-guiapp_1.0~1_all
thomas@thomas-VirtualBox:~/harthm17-guiapp_1.0~1_all$
```

### Schritt 3 - Kopievon Datei DEBIAN/control
Nun erstellen wir einen Unterordner "DEBIAN" in diesem wird sich unsere "control" Datei befinden.
```
thomas@thomas-VirtualBox:~/harthm17-guiapp_1.0~1_all$ mkdir DEBIAN
thomas@thomas-VirtualBox:~/harthm17-guiapp_1.0~1_all$ cd DEBIAN
thomas@thomas-VirtualBox:~/harthm17-guiapp_1.0~1_all/DEBIAN$ nano control
```

Der folgende Teil muss in die control Datei eingefügt werden.
```
Package: harthm17-guiapp
Version: 1.0~1 
Architecture: all 
Depends: default-jre (>=2:1.11) 
Installed-Size: 36
Maintainer: Thomas Harrer <harthm17@htl-kaindorf.at>
Description: My first Java GUI Application
```
Das Version wurde von mir extra hinzugefügt.

### Schritt 4 - Datei DEBIAN/postinst und DEBIAN/postrm


### Schritt 5 - Java Programm einfügen

### Schritt 6 - Paketdokumentation

### Schritt 7 - Paketgröße in DEBIAN/control korrigieren

### Schritt 8-9
Diese zwei Schritte wurden nicht mehr erledigt.

## Feedback

