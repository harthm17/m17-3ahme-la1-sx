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
In unseren Ordner können verschiedene Scipt-Datein angelegt werden, die bei der Installation oder Deinstallation ausgeführt werden.
Folgende Datein sind möglich:
* preinst (wird am Anfang der Installation, bevor Dateien entpackt werden, ausgeführt)
* postinst (wird am Ende der Installation, nachdem Dateien entpackt werden, ausgeführt)
* prerm (wird am Anfang der Deinstallation, bevor Dateien gelöscht werden, ausgeführt)
* postrm (wird am Ende der Installation, nachdem Dateien gelöscht wurden, ausgeführt)

Nun werden wir eine postinst und eine postrm Datei erstellen. Diese haben wir in unserem DEBIAN Ordner erstellt.
```
thomas@thomas-VirtualBox:~/harthm17-guiapp_1.0~1_all/DEBIAN$ touch postinst
thomas@thomas-VirtualBox:~/harthm17-guiapp_1.0~1_all/DEBIAN$ chmod +x postinst
thomas@thomas-VirtualBox:~/harthm17-guiapp_1.0~1_all/DEBIAN$ nano postinst
```
Bei der postrm Datei muss statt "postinst" "postrm" geschrieben werden.
Der Inhalt er postinst Datei sieht so aus:
```
#!/bin/sh 
set -e 
set -x

printf '%b' "\033[32;1m [INFO] harthm17-guiapp (postinst) -> $0 $1 \033[0m\n"
```

### Schritt 5 - Java Programm einfügen
Der nächste Schritt ist es das Java Programm von /home/thomas/NetBeansProjects/harthm17/dist/harthm17.java (dies ist mein Pfad für die .java Datei) in usr/share/harthm17-huiapp/.
Der Pfad usr/share/hartm17-huiapp/ wird in harthm17-guiapp_1.0~1_all/ angelegt.
```
thomas@thomas-VirtualBox:~/harthm17-guiapp_1.0~1_all/DEBIAN$ cd ..
thomas@thomas-VirtualBox:~/harthm17-guiapp_1.0~1_all$ mkdir -p usr/share/harthm17-guiapp
thomas@thomas-VirtualBox:~/harthm17-guiapp_1.0~1_all$ cp /home/thomas/NetBeansProjects/harthm17/dist/harthm17.java usr/share/hartm17-huiapp/
```

Nun erstellen wir eine .desktop Datei mit Hilfe des Terminal Editors. Die Datei ist dafür zuständig das es im Ubuntu System als GUI Applikation gefunden wird.
```
thomas@thomas-VirtualBox:~/harthm17-guiapp_1.0~1_all$ mkdir usr/share/applications
thomas@thomas-VirtualBox:~/harthm17-guiapp_1.0~1_all$ nano harthm17-guiapp.desktop
```

Die .desktop muss mit diesem Inhalt befüllt werden.
```
[Desktop Entry]
Name=harthm17-java-application
GenericName=harthm17 Java Gui Application
GenericName[de]=harthm17 Java Gui Applikation
Comment=My first Java GUI Application for Ubuntu
Exec=java -jar /usr/share/applications/harthm17.jar
Icon=/usr/share/harthm17-guiapp/icon.png
Terminal=false
Type=Application
StartupNotify=false
```

Bei Icon=/usr/share/harthm17-guiapp/icon.png muss man ein Icon (Bild) erstellen.
Dies habe ich nicht erledigt da in meinen Augen die Übung wichtiger ist.
Wenn man dies aber macht muss man das Bild unter diesem Pfad speichern.
Das Bild muss ausßerdem nicht "icon" heißen sonder kann einen beliebigen Namen haben, dieser muss jedoch auch in der .desktop Datei stehen.

### Schritt 6 - Paketdokumentation


### Schritt 7 - Paketgröße in DEBIAN/control korrigieren


### Schritt 8-9
Diese zwei Schritte wurden nicht mehr erledigt.

## Feedback
Der Inhalt wurde verstanden und es gab keine großen Probleme.
Es gab ab und an Probleme mit der Speicheradresse oder generel mit Adressen aber diese konnten schnell behoben werden.
