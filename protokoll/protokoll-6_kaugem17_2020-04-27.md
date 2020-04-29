# 6. Protokoll

-------------------------------------------------

## Thema: Debian Paket erzeugen

-------------------------------------------------

Übungsdatum:   Montag, 27.04.2020     
Übungszeit:    14:10 bis 16:30      
Übungsort:     St. Veit in der Südsteiermark, Home-Office    
Verfasser:     Georg Kaufmann    
Abwesend:      keiner      
Anwesend:      Felix Hamrle, Stefan Haring, Thomas Harrer, Georg Kaufmann, Andreas Kogler, Franz Lieleg, Simon Marcher

-------------------------------------------------

### Inhaltsverzeichnis
1) [Java Programm erstellen](#java-programm-erstellen) 
1) [Debian Paketverzeichnis erstellen](#debian-paketverzeichnis-erstellen)
1) [Datei DEBIAN/control](#datei-debiancontrol)
1) [Datei DEBIAN/postints und DEBIAN/postrm](#datei-debianpostints-und-debianpostrm)
1) [Java Programm einfügen](#java-programm-einfügen)
1) [Resümee](#resümee)

-------------------------------------------------

#### Java Programm erstellen
Es ist mit Netbeans ein Java Swing GUI Programm zu erstellen.
Dazu ist es ratsam sich folgendes [Video](https://cloud.htl-mechatronik.at/index.php/s/AlyXs7YglQDLZSP) anzuschauen.

Hier nochmals kurz zusammen gefasst. Hierbei muss man folgende Schritte beachten und umsetzen:
1) Java Projekt erzeugen
1) Java Paket gui erzeugen
1) Java Klasse abgeleitet von jFrame erzeugen
1) Titel und Mindestgröße konfigurieren, Fenster in der Bildschirmmitte öffnen lassen
1) "Flow Layout" setzen
1) Button "Press me..." einfügen
1) Im Button-Handler-Methode ein Dialogfenster öffnen und einen Text ausgeben
1) Projekt ausführen und testen
1) Projekt mit "Clean and Build" übersetzen
1) Aus dem Ordner dist die fertige Java Archiv Datei entnehmen

-------------------------------------------------

#### Debian Paketverzeichnis erstellen
Es ist ein Unterordner für das Debianpaket zu erstellen.
```
user@host:~$ mkdir kursname-guiapp_1.~1_all
user@host:~$ cd kursname-guiapp_1.~1_all
user@host:~/kursname-guiapp_1.~1_all$
```
Es werden bereits drei Informationen bekannt gegeben.
1) Der Name des Pakets (kursname-guiapp).
2) Die Version des Pakets. In unserem Fall 1.0~1.
3) Die unterstützte Architektur. In unserem Fall **all**, was bedeutet das alle Architekturen unterstützt werden.

-------------------------------------------------

#### Datei DEBIAN/control
Nun ist ein Unterordner **DEBIAN** zu erstellen. In diesem **muss** sich eine Datei **control** befinden.
```
user@host:~/kursname-guiapp_1.~1_all$ mkdir DEBIAN
user@host:~/kursname-guiapp_1.~1_all$ cd DEBIAN
user@host:~/kursname-guiapp_1.~1_all/DEBIAN$ nano control 
```
Diese Datei control ist mit folgendem Text zu befüllen
```
Package: kursname-guiapp
Architecture: all
Depends: default-jre (>=2:1.11)
Installed-Size: 1000
Maintainer: Georg Kaufmann <kaugem17@htl-kaindorf.at>
Description: My first Java GUI Application
```
Die Informationen müssen angepasst werden.

-------------------------------------------------

#### Datei DEBIAN/postints und DEBIAN/postrm
Zusätzlich können verschiedene Script-Dateien im Ordner DEBIAN abgelegt werden. Diese werden bei der Installation bzw. Deinstallation ausgeführt.

| Script-Datei |    |
| ------------ | -- |
| ```preinst``` | wird am Anfang der Installation, bevor Dateien entpackt werden, ausgeführt |
| ```postinst``` | wird am Ende der Installation, nachdem Dateien entpackt werden, ausgeführt |
| ```prerm```| wird am Anfang der Deinstallation, bevor Dateien gelöscht werden, ausgeführt |
| ```postrm```| wird am Ende der Installation, nachdem Dateien gelöscht wurden, ausgeführt |

Als Beispiel erstellen wir die postinst. Man muss darauf Achten, dass die Dateien im Ordner DEBIAN gespeichert werden.
```
user@host:~/kursname-guiapp_1.~1_all/DEBIAN$ touch postinst
user@host:~/kursname-guiapp_1.~1_all/DEBIAN$ chmod +x postinst
user@host:~/kursname-guiapp_1.~1_all/DEBIAN$ nano postinst
```
Es muss folgender Inhalt eingefügt werden.
```
#!/bin/sh
#set -e
#set -x

printf '%b' "\033[32;1m [INFO] kursname-guiapp (postinst) -> $0 $1 \033[0m\n"
```

-------------------------------------------------

#### Java Programm einfügen
Später werden alle im Paket enthaltenen Verzeichnisse und Dateien, mit Ausnahme des Ordner DEBIAN, bei der Installation 1:1 auf das Zielsystem kopiert. Es werden jedoch weder der Eigentümer noch die Rechte oder das Datum verändert.
Nach der Installation soll sich das Java Programm im Ordner ```/usr/share/kursname-guiapp```
befinden. Dazu muss man folgendes Umsetzen. 
```
user@host:~/kursname-guiapp_1.~1_all/DEBIAN$ cd ..
user@host:~/kursname-guiapp_1.~1_all$ mkdir -p usr/share/kursname-guiapp
user@host:~/kursname-guiapp_1.~1_all$ cp .../MyGuiApp/dist/*.jar usr/share/kursname-guiapp/
```
-p ermöglicht das gleich mehrere Verzeichnisse auf einmal erzeugt werden.
Da wir die Datei im Unterordner haben möchten, müssen wir einen relativen Pfad angeben. (mit einem / am Start wäre dies ein absoluter Pfad) 
Nun muss ein Unterverzeichnis ```usr/share/applications``` erstellt werden.
```
user@host:~/kursname-guiapp_1.~1_all$ mkdir usr/share/applications
user@host:~/kursname-guiapp_1.~1_all$ nano kursname-guiapp.desktop
```
Dort ist nun folgeder Inhalt einzugügen.
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
Es muss alles angepasst werden. Anschließend ist noch ein Icon für dein Programm zu erstellen (mit z.B. gimp oder gpaint). Dies muss dann im richtigen Ordner abgelegt werden.

-------------------------------------------------

#### Resümee
Ich bin bis Punkt fünf gekommen und hatte einige Probleme. 
