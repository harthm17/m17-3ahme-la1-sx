# Protokoll-6 LABOR/SX 3AHME (2019/20)

* **Thema:** Debian Paket erzeugen
* **Datum:** 27.04.2020
* **Gefehlt:** Keiner
* **Erstellt von:** koganm17
* **Protokoll letzte Einheit:** [20.04.2020](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/koganm17/Protokolle/Protokoll-5_koganm17_2020-04-20.md)

----------------------------------------------------------------------------------------------

## Inhaltsverzeichnis
1) [Informationen](#informationen)
1) [Übung 1 Debian Paket erzeugen](#übung-1-debian-paket-erzeugen)
1) [Feedback](#feedback)
         
----------------------------------------------------------------------------------------------
 
 ## Informationen
 
 Unser erster Arbeitsauftrag war es folgende Kapitel im Linux 2 Skript im Lms durchzulesen.
 * [Kapitel 3](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#472857424)
 * [Kapitel 3.1](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#472937916)
 
 In diesen Kapiteln ging es um Installationspakete, Tools und Konfigurationsdateien.
 
 Unser zweiter Arbeitsauftrag war Übung 1 im [Kapitel 3.2](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#473068402)
 
 In dieser Übung erzeugen wir ein Debian Paket.
 
 Für den zweiten Arbeitsauftrag, Schritt 1 bekamen wir zur Hilfestelung [dieses Video](https://cloud.htl-mechatronik.at/index.php/s/AlyXs7YglQDLZSP) Dieses video zeigte wie man ein Java Swing GUI Programm erstellt.
 
 ----------------------------------------------------------------------------------------------
 
 ## Übung 1 Debian Paket erzeugen
 [Hier](https://cloud.htl-mechatronik.at/index.php/s/AlyXs7YglQDLZSP) ist die Anlteitung. 
 
 ### Schritt 1 - Java Programm erstellen
 Für Schritt 1 haben wir [dieses Video](https://cloud.htl-mechatronik.at/index.php/s/AlyXs7YglQDLZSP) als Hilfestellung bekommen.
 Folgende Schritte mussten erledigt werden: 
1) Java Projekt erzeugen
1) Java Paket gui erzeugen
1) Java Klasse abgeleitet von JFrame erzeugen (Netbeans JFrame Form ...)
1) Titel und Mindestgröße konfigurieren, Fenster in der Bildschirmmitte öffnen lassen
1) "Flow Layout" setzen
1) einen Button "Press me..." einfügen
1) In der Button-Handler-Methode ein Dialogfenster öffnen und einen Text ausgegeben
1) Das Projekt ausführen und testen
1) Das Projekt mit "Clean und Build" übersetzen
1) Aus dem Ordner dist die fertige Java Archiv Datei entnehmen

 ### Schritt 2 - Debian Paketverzeichnis erstellen
 Nun erstellen wir einen Unterordner für das zu erstellende Debianpaket.
 ```
user@host:~$ mkdir sx-guiapp_1.0~1_all
user@host:~$ cd sx-guiapp_1.0~1_all
user@host:~/sx-guiapp_1.0~1_all$ 
 ```
Dabei muss man darauf achten, den Kurznamen statt sx zu verwenden. 

 ### Schritt 3 - Kopie von Datei DEBIAN/control
 Nun erstellen wir einen Unterordner DEBIAN indem sich die Datei control befinden muss.
 ```
user@host:~/sx-guiapp_1.0~1_all$ mkdir DEBIAN
user@host:~/sx-guiapp_1.0~1_all$ cd DEBIAN
user@host:~/sx-guiapp_1.0~1_all/DEBIAN$ nano control
 ```
 Diese Datei wird mit folgendem Inhalt befüllt.
 ```
Package: sx-guiapp
Architecture: all
Depends: default-jre (>=2:1.11)
Installed-Size: 1000
Maintainer: Manfred Steiner <sx@htl-kaindorf.ac.at>
Description: My first Java GUI Application
```
Dabei muss man darauf achten, den Kurznamen statt sx zu verwenden.  
Wir haben jedoch einen weiteren eintrag hinzufügen müssen.
``` 
Version: 1.0~1
```

 ### Schritt 4 - Datei DEBIAN/postinst und DEBIAN/postrm
 Optional können im Ordner DEBIAN Script-Dateien abgelegt werden, die bei der Installation oder Deinstallation ausgeführt werden. Folgende Dateien sind möglich:
* preinst (wird am Anfang der Installation, bevor Dateien entpackt werden, ausgeführt)
* postinst (wird am Ende der Installation, nachdem Dateien entpackt werden, ausgeführt)
* prerm (wird am Anfang der Deinstallation, bevor Dateien gelöscht werden, ausgeführt)
* postrm (wird am Ende der Installation, nachdem Dateien gelöscht wurden, ausgeführt)

Wir haben eine postinst und eine postrm Datei erstellt. Diese haben wir im Ordner Debian erstellt und mit einem vorgegebenen Inhalt befüllt.
Befehle:
```
user@host:~/sx-guiapp_1.0~1_all/DEBIAN$ touch postinst
user@host:~/sx-guiapp_1.0~1_all/DEBIAN$ chmod +x postinst
user@host:~/sx-guiapp_1.0~1_all/DEBIAN$ nano postinst
```
Bei der postrm Datei muss man statt postinst postrm schreiben.
Inhalt der Dateien
```
#!/bin/sh
#set -e
#set -x

printf '%b' "\033[32;1m [INFO] sx-guiapp (postinst) -> $0 $1 \033[0m\n"
```


 ### Schritt 5 - Java Programm einfügen
 Hier kopieren wir das javaProgramm von .../MyGuiApp/dist/*.jar in usr/share/sx-guiapp/.
 ```
user@host:~/sx-guiapp_1.0~1_all/DEBIAN$ cd ..
user@host:~/sx-guiapp_1.0~1_all$ mkdir -p usr/share/sx-guiapp
user@host:~/sx-guiapp_1.0~1_all$ cp .../MyGuiApp/dist/*.jar usr/share/sx-guiapp/
```
 
 Nun erstellen wir eine .desktop Datei, damit das Programm in einem Ubuntu System als GUI Applikation gefunden wird.
 ```
user@host:~/sx-guiapp_1.0~1_all$ mkdir usr/share/applications
user@host:~/sx-guiapp_1.0~1_all$ nano sx-guiapp.desktop
```
Diese Datei befüllen wir wieder mit folgendem Inhalt.
```
[Desktop Entry]
Name=sx-java-application
GenericName=SX Java Gui Application
GenericName[de]=SX Java Gui Applikation
Comment=My first Java GUI Application for Ubuntu
Exec=java -jar /usr/share/sx-guiapp/MyJavaApplication.jar
Icon=/usr/share/sx-guiapp/icon.png
Terminal=false
Type=Application
StartupNotify=false
```
Dabei muss man darauf achten, den Kurznamen statt sx zu verwenden.  
 
 ### Schritt 6 - Paketdokumentation
Im Unterordner /usr/share/doc sind Paketinformationen für alle Pakete zu finden.
Wir legen daher in unserem Paketverzeichnis folgende Ordner und Dateien an:
```
user@host:~/sx-guiapp_1.0~1_all$ mkdir -p usr/share/doc/sx-guiapp
user@host:~/sx-guiapp_1.0~1_all$ touch usr/share/doc/sx-guiapp/changelog
user@host:~/sx-guiapp_1.0~1_all$ touch usr/share/doc/sx-guiapp/copyright
```
Die Datei changelog befüllen wir mit folgendem Inhalt (nano changelog)
```
sx-guiapp (1.0~1) stable; urgency=low

  * creating debian package

  -- Manfred Steiner <sx@htl-kaindorf.ac.at>  Mon, 27 Apr 2020 15:00:00 +0100
```
und die Datei copyright befüllen wir mit diesem Inhalt (nano copyright)
```
Format: http://www.debian.org/doc/packaging-manuals/copyright-format/1.0/
Upstream-Name: sx-guiapp

Files: * Copyright: 2020 Manfred Steiner <sx@htl-kaindorf.at>
License: GPL-3+ License: GPL-3+

 This program is ... 
 ...
 On Debian systems, the complete text of the GNU Lesser General
 Public License version 3 can be found in
 "/usr/share/common-licenses/LGPL-3".
```
Wir müssen wieder darauf achten, die richtigen Daten zu verwenden.

### Schritt 7 - 9
Zu diesen Schritten bin ich leider nicht mehr gekommen. In diesen Schritten hätten folgendes gemacht:
* Paketgröße in DEBIAN/control korrigieren
* Paket erzeugen
* Paket installieren

 ----------------------------------------------------------------------------------------------
## Feedback

Der Inhalt wurde durchaus verstanden und es gab auch bei keinem Punkt schwerwiegende Probleme.

Am Anfange hatte ich jedoch Problem mit Virtualbox.

Diese Probleme liesen sich durch andere Einstellungen mit Hilfe von Herrn Steiner kompensieren. 

Ohne diese Probleme wäre ich womöglich noch bis Schritt 7 oder 8 gekommen.

