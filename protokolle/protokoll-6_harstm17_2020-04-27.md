 # Protokoll-6 LABOR/SX 3AHME (2019/20)

---------------------------------------------------------------------------------------------

* **Thema:** Debian Paket erzeugen
* **Datum:** 27.04.2020
* **Gefehlt:** -
* **Erstellt von:** Stefan Haring (harstm17)
* **Protokoll der letzten Einheit:** [Protokoll 5](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/harstm17/protokolle/protokoll-5_harstm17_2020-04-20.md)

----------------------------------------------------------------------------------------------

## Inhaltsverzeichnis  

1. [Allgemeines](#allgemeines)
1. [Debian Paket erzeugen](#debian-paket-erzeugen)
1. [Resümee](#resümee)

---------------------------------------------------------------------------------------------

### Allgemeines
 
* Unser erster Arbeitsauftrag war es folgende Kapitel im Linux 2 Skript, welches sich auf LMS befindet durchzulesen.
     * [Kapitel 3](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#472857424)
     * [Kapitel 3.1](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#472937916)
     
     Im gesamten Kapitel 3 geht es um jene Techniken, die in Debian- und Ubuntu Systemen (und Subsystemen) verwendet werden, um Software      zu installieren.
 
* Unser zweiter Arbeitsauftrag war es, sich die Theorie aus dem vorher Durchgelesenem in Übung 1 im [Kapitel 3.2](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#473068402) zu nutze zu machen. In dieser Übung galt es, ein Debian Paket zu erzeugen. Falls Interesse an genaueren Informationen zu den jeweiligen Schritten vorliegt, soll bitte am obigen Link nachgeschaut werden.
 
 ----------------------------------------------------------------------------------------------
 
 ### Übung 1 Debian Paket erzeugen
 
 [Hier](https://cloud.htl-mechatronik.at/index.php/s/AlyXs7YglQDLZSP) kann man die schriftliche Anleitung aufrufen.
 
 #### Schritt 1 - Java Programm erstellen

Um Schritt 1 gut durchführen zu können, hilft [dieses sehr hilfreiche Tutorial](https://cloud.htl-mechatronik.at/index.php/s/AlyXs7YglQDLZSP) bestimmt weiter. Dieses video zeigte wie man ein Java Swing GUI Programm in NetBeans  korrekt erstellt. Wichtig ist es, die neueste Aktualisierung der IDE zu haben, damit keine Bugs oder Sondergleichen auftreten.

Folgende Schritte mussten erledigt werden: 
1. Java Projekt erzeugen
1. Java Paket gui erzeugen
1. Java Klasse abgeleitet von JFrame erzeugen (Netbeans JFrame Form ...)
1. Titel und Mindestgröße konfigurieren, Fenster in der Bildschirmmitte öffnen lassen
1. "Flow Layout" setzen
1. einen Button "Press me..." einfügen
1. In der Button-Handler-Methode ein Dialogfenster öffnen und einen Text ausgegeben
1. Das Projekt ausführen und testen
1. Das Projekt mit "Clean und Build" übersetzen
1. Aus dem Ordner dist die fertige Java Archiv Datei entnehmen

 #### Schritt 2 - Debian Paketverzeichnis erstellen
 
 Nun erstellen wir einen Unterordner für das zu erstellende Debianpaket. Es darf nicht darauf vergessen zu werden, dass statt ***sx*** das jeweilige Kürzel eingesetzt wird.
 ```
user@host:~$ mkdir sx-guiapp_1.0~1_all
user@host:~$ cd sx-guiapp_1.0~1_all
user@host:~/sx-guiapp_1.0~1_all$ 
 ```
 
 #### Schritt 3 - Kopie von Datei DEBIAN/control
 
Nun erstellen wir einen weiteren Unterordner *DEBIAN* indem sich die Datei *control*, nach dem Eingeben der folgenden Kommandos befinden muss. 
 ```
user@host:~/sx-guiapp_1.0~1_all$ mkdir DEBIAN
user@host:~/sx-guiapp_1.0~1_all$ cd DEBIAN
user@host:~/sx-guiapp_1.0~1_all/DEBIAN$ nano control
 ```
 Diese Datei wird mit folgendem Paketinformationen befüllt.
 ```
Package: sx-guiapp
Architecture: all
Depends: default-jre (>=2:1.11)
Installed-Size: 1000
Maintainer: Manfred Steiner <sx@htl-kaindorf.ac.at>
Description: My first Java GUI Application
```
Dabei muss man erneut darauf achten, den Kurznamen statt sx zu verwenden. 

Folgend musste herausgefunden werden, welcher Eintrag noch fehlt. Laut meines Ermessens, müsste das folgender Text sein:
``` 
Version: 1.0~1
```

#### Schritt 4 - Datei DEBIAN/postinst und DEBIAN/postrm

```
user@host:~/sx-guiapp_1.0~1_all/DEBIAN$ touch postinst
user@host:~/sx-guiapp_1.0~1_all/DEBIAN$ chmod +x postinst
user@host:~/sx-guiapp_1.0~1_all/DEBIAN$ nano postinst
```
Mit den obigen Befehlen haben wir eine *postinst*-Datei erstellt. Diese haben im Ordner *Debian* ihre Verzeichniswurzel und anschließend werden sie mit vorgegebenen Inhalt befüllt:
```
#!/bin/sh
#set -e
#set -x

printf '%b' "\033[32;1m [INFO] sx-guiapp (postinst) -> $0 $1 \033[0m\n"
```
Erneut muss hier statt *sx* der Kurzname eingegeben werden.

#### Schritt 5 - Java Programm einfügen

 Hier kopieren wir das Java-Programm von .../MyGuiApp/dist/*.jar in usr/share/sx-guiapp/.
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
Wie schon mehrmals beschrieben, muss hier wieder das Kürzel statt *sx* verwendung finden. 
 
#### Schritte 6-9

Diese Schritte waren mir aufgrund mangelnder Zeit nicht möglich zu erarbeiten.

----------------------------------------------------------------------------------------------
 
### Resümee

Die Übung wurde ohne grobe Probleme durchgeführt, jedoch gab es mit der Abgabe auf LMS Unklarheiten, die nicht 100%ig behoben werden konnten.
