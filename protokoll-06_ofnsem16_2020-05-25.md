# 6. Protokoll
------------------------------------
## Thema: Debian Paket erzeugen
------------------------------------
* Datum:      25.05.2020
* Gruppe:     3
* Abwesend:   keiner
* Verfasser:  Ofner Sebastian
* Klasse:     3AHME/AHME17
* Schuljahr:  2019/20
------------------------------------
## Inhaltsverzeichnis
* [Control](#control)
* [Debian/postinst und Debian/postrm](#debian/postinst-und-debian/postrm)
* [Java Programm einfügen](#java-programm-einfügen)
* [Paketdokumentation](#paketdokumentation)
* [Paketgröße in Debian/control korrigieren](#paketgröße-in-debian/control-korrigieren)
* [Paket erzeugen](#paket-erzeugen)
* [Paket installieren](#paket-installieren)
------------------------------------
### Control
Ich bin in der letzten Einheit hier hängen geblieben. Wir mussten die Datei Control erstellen. In unserer Angabe fehlte jedoch eine Zeile, die wir auf [dieser Seite](https://www.debian.org/doc/debian-policy/ch-controlfields.html) herausfinden sollten. 
Es fehlte noch die Zeile **Version**, die am Ende hinzugefügt werden musste.       Die Datei sieht dann so aus:
```
Package: ofner-guiapp
Architecture: all
Depends: default-jre (>=2:1.11)
Installed-Size: 1000
Maintainer: Ofner Sebastian <ofnsem16@htl-kaindorf.ac.at>
Description: My first Java GUI Application
Version: 1.0
```
### Debian/postinst und Debian/postrm
Wir sollten 2 Script-Dateien im **Debien-Ordner** anlegen, die sind zwar für unsere Anwendung nicht zwingend notwendig, doch wir können sie beim
Starten beobachten.

Die erste der beiden ist die **postinst**-Datei. 
Um sie zu erstellen müssen folgende Befehle in die Konsole eingeben:
```
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all/DEBIAN$ touch postinst
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all/DEBIAN$ chmod +x postinst
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all/DEBIAN$ nano postinst
```
In diese Datei war folgendes zu schreiben:
```
#!/bin/sh
#set -e
#set -x

printf '%b' "\033[32;1m [INFO] ofner-guiapp (postinst) -> $0 $1 \033[0m\n"
```
Was die Steuerzeichen bedeuten, kann man [hier](https://stackoverflow.com/questions/4842424) nachlesen. 
Die Anweisung **-e** und **-x** sind hier deaktiviert, können aber zur Fehlersuche genutzt werden. 


Die zweite Datei ist die **postrm**-Datei.
Um diese zu erstellen (ähnlich wie bei der ersten Datei) muss folgendes in die Konsole eingegeben werden:
```
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all/DEBIAN$ touch postrm
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all/DEBIAN$ chmod +x postrm
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all/DEBIAN$ nano postrm
```
Die Datei war mit Folgenden zu befüllen:
```
#!/bin/sh
#set -e
#set -x

printf '%b' "\033[32;1m [INFO] sx-guiapp (postrm) -> $0 $1 \033[0m\n"
```

### Java Programm einfügen
Als nächstes mussten wir das Java-Programm in unseren Ordner einfügen. Dazu müssen wir diese Befehle eingeben:
```
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all/DEBIAN$ cd ..
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all$ mkdir -p usr/share/ofner-guiapp
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all$ cp .../MyGuiApp/dist/*.jar usr/share/ofner-guiapp/
```
Als nächstes mussten wir die **.desktop**-Datei erzeugt werden. Dazu dienen folgende Befehle:
```
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all$ mkdir usr/share/applications
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all$ nano ofner-guiapp.desktop
```
Die war mit Folgenden zu befüllen:
```
[Desktop Entry]
Name=ofner-java-application
GenericName=Ofner Java Gui Application
GenericName[de]=Ofner Java Gui Applikation
Comment=My first Java GUI Application for Ubuntu
Exec=java -jar /usr/share/ofner-guiapp/MyJavaApplication.jar
Icon=/usr/share/ofner-guiapp/icon.png
Terminal=false
Type=Application
StartupNotify=false
```
Theoretische Informationen findet man [hier](https://wiki.ubuntuusers.de/.desktop-Dateien/).

### Paketdokumentation
Wir sollten folgende Dateien im ordner **/usr/share/doc** anlegen, um Paketinformationen zu speichern.
Um diese zu erstellen sind folgende Befehle notwendig:
```
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all$ mkdir -p usr/share/doc/ofner-guiapp
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all$ touch usr/share/doc/ofner-guiapp/changelog
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all$ touch usr/share/doc/ofner-guiapp/copyright
```

In die Datei **changelog** gehört Folgendes:
```
ofner-guiapp (1.0~1) stable; urgency=low

  * creating debian package

  -- Ofner Sebastian <ofnsem16@htl-kaindorf.ac.at>  Mon, 25 Mai 2020 15:00:00 +0100
  ```

In die Datei **copyright** gehört Folgendes:
```
Format: http://www.debian.org/doc/packaging-manuals/copyright-format/1.0/
Upstream-Name: ofner-guiapp

Files: * Copyright: 2020 Ofner Sebastian <ofnsem16@htl-kaindorf.at>
License: GPL-3+ License: GPL-3+

 This program is ... 
 ...
 On Debian systems, the complete text of the GNU Lesser General
 Public License version 3 can be found in
 "/usr/share/common-licenses/LGPL-3".
 ```

### Paketgröße in Debian/control korrigieren
Als wir die control-Datei anlegten machten wir die **Installed Size** absichtlich viel zu groß. Die müssen wir jetzt auf den richtigen Wert ändern. Um die Größe herauszufinden und zu ändern dienen folgende Befehle:
```
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all$ du -sb usr
571152    usr
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all$ du -s usr
564 usr
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all$ nano DEBIAN/control
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all$ cat DEBIAN/control
Package: ofner-guiapp
...
Installed-Size: 564
...
```

### Paket erzeugen
Um das Programm später installieren zu können, muss eine Kopie erzeugt werden, und die Eigentümerschaft geändert werden. 
Dazu müssen folgende Befehle als Superuser eingegeben werden:
```
sebastian@sebastian-VirtualBox:~/ofner-guiapp_1.0~1_all$ sudo -i
root@sebastian-VirtualBox:~# rsync -aP /home/sebastian/ofner-guiapp_1.0_all ./
root@sebastian-VirtualBox:~# chown -R root:root ofner-guiapp_1.0_all
root@sebastian-VirtualBox:~# dpkg --build ofner-guiapp_1.0_all
dpkg-deb: Paket »sx-guiapp« wird in »ofner-guiapp_1.0~1_all.deb« gebaut.
root@sebastian-VirtualBox:~# ls -l *.deb
-rw-r--r-- 1 root root 3216 Apr 27 15:20 ofner-guiapp_1.0~1_all.deb
```
### Paket installieren
Jetzt können wir als Superuser das Paket mit diesen Befehlen installieren:
```
root@sebastian-VirtualBox:~# dpkg --install ofner-guiapp_1.0_all.deb
(Lese Datenbank ... 250962 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von ofner-guiapp_1.0~1_all.deb ...
Entpacken von ofner-guiapp (1.0~1) über (1.0~1) ...
 [INFO] ofner-guiapp (postrm) -> /var/lib/dpkg/info/ofner-guiapp.postrm upgrade
ofner-guiapp (1.0~1) wird eingerichtet ...
 [INFO] ofner-guiapp (postinst) -> /var/lib/dpkg/info/ofner-guiapp.postinst configure
```
Das hat bei mir fehlerfrei funktioniert.

Ich habe dann bei Übung 2 die erste Aufgabe versucht, bin aber durch einen Denkfehler (den ich inzwischen gefunden habe), nicht wirklich zu einem Ergebnis gekommen. 
