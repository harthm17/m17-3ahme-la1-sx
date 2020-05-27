# Protokoll 6 Labor-SX (2019/20)

---------------------------------------------------

* **Erstellt von:** Vanessa Plieschnegger
* **Datum:** 25.05.2020
* **Thema:** Ausarbeitung der Aufgabenstellung
* **Fehlend:** keiner

---------------------------------------------------

## Inhaltsverzeichnis
1. [Erstellung einer Java GUI Applikation](#erstellung-einer-java-gui-applikation)
2. [Debian Paketverzeichnis erstellen](#debian-paketverzeichnis-erstellen)
3. [DEBIAN control Datei erstellen](#debian-control-datei-erstellen)
4. [DEBIAN postinst Datei erstellen](#debian-postinst-datei-erstellen)
5. [Java Programm einfügen](#java-programm-einfügen)
6. [Paketdokumentation](#paketdokumentation)
7. [Paketgröße in DEBIAN control korrigieren](#paketgröße-in-debian-control-korrigieren)
8. [Paket erzeugen](#paket-erzeugen)
9. [Paket installieren](#paket-installieren)

---------------------------------------------------

### Erstellung einer Java GUI Applikation
Zuerst einmal muss auf Netbeans 11.3 ein Projekt namens MyJavaGuiApp.
Nun muss man ein Java Paket anlegen namens gui.
Nun muss man eine Klasse erstellen. Mir nehmen die JFrame Form und nennen diese MainGui.
Jetzt müssen wir das Layout auf ein FLow Layout ändern.
Nun erstellen wir einen Button welchen wir "Press me..." nennen.
Wenn man will kann man das Programm jetzt einmal ausführen.
Im Source code kann man nun unter initComponents(); den Bfehel
```
setTitle("PlieschneggerVanessa Meine Java GUI Applikation")
```
verwenden, um dem Programm einen Titel zu geben. Wenn man nun noch den Befehl
```
setLocationRealtiveTo(null)
```
und den Befehl
```
setMinimumSize(new DImension(300, 200)
```
benutz, dann man gleich eine viel schöner Ausgabe, welche auch von den Dimensionen her passt.
Nun müssen wir noch eine Händlermethode hinzufügen, dies geht ganz einfach, da man nur einen Doppelklick auf den Button machen muss und schon
wird eine fertige Funktion angelegt. Unter diesem Befehl der im Source code neu aufgetauch ist, schreibt man nun folgenden Befehl:
```
JOptionPane.showMessageDialog(
    this,
    "Button wurde gedrückt",
    "Nachricht ...",
    JOptionPane.INFORMATION_MESSAGE
    );
```
Nun ist das Programm fertig!

### Debian Paketverzeichnis erstellen
Um ein Debian Paketverzeichnis zu erstellen, muss man nur folgende Befehle eingeben:
```
user@host:~$ mkdir PlieschneggerVanessa-guiapp_1.0~1_all
user@host:~$ cd PlieschneggerVanessa-guiapp_1.0~1_all
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all$
```

### DEBIAN control Datei erstellen
Um eine DEBIAN/control Datei zu erstellen, muss man zunächst einmal die folgenden Befehle ausführen:
```
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all$ mkdir DEBIAN
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all$ cd DEBIAN
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all/DEBIAN$ nano control
```
Nun muss man mittel nano die Steuerdatei control mit folgendem befüllen:
```
Package: PlieschneggerVanessa-guiapp
Architecture: all
Depends: default-jre (>=2:1.11)
Installed-Size: 1000
Maintainer: Vanessa Plieschnegger <plivac17@htl-kaindorf.at>
Description: My first Java GUI Application
Version: 1.0
```

### DEBIAN postinst Datei erstellen
Um solch eine Datei zu erstellen muss man folgende Befehle ausführen:
```
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all/DEBIAN$ touch postinst
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all/DEBIAN$ chmod +x postinst
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all/DEBIAN$ nano postinst
```
Nun muss man die Datei postinst noch mit folgendem Inhalt befüllen:
```
#!/bin/sh
#set -e
#set -x

printf '%b' "\033[32;1m [INFO] PlieschneggerVanessa-guiapp (postinst) -> $0 $1 \033[0m\n"
```

### Java Programm einfügen
Um ein Java Programm einzufügen sollte man folgende Befehle befolgen:
```
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all/DEBIAN$ cd ..
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all$ mkdir -p usr/share/PlieschneggerVanessa-guiapp
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all$ cp .../MyGuiApp/dist/*.jar usr/share/PlieschneggerVanessa-guiapp
```
```
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all$ mkdir usr/share/applications
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all$ nano PlieschneggerVanessa-guiapp.desktop
```
Nun müssen wir die PlieschneggerVanessa-guiapp.desktop Datei noch mit folgendem Inhaalt befüllen:
```
[Desktop Entry]
Name=PlieschneggerVanessa-java-application
GenericName=PlieschneggerVanessa Java Gui Application
GenericName[de]=PlieschneggerVanessa Java Gui Applikation
Comment=My first Java GUI Application for Ubuntu
Exec=java -jar /usr/share/PlieschneggerVanessa-guiapp/MyJavaApplication.jar
Icon=/usr/share/PlieschneggerVanessa-guiapp/icon.png
Terminal=false
Type=Application
StartupNotify=false
```

### Paketdokumentation
Um die Paketdokumentation zu erstellen muss man folgende Befehle befolgen:
```
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all$ mkdir -p usr/share/doc/PlieschneggerVanessa-guiapp
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all$ touch usr/share/doc/PlieschneggerVanessa-guiapp/changelog
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all$ touch usr/share/doc/PlieschneggerVanessa-guiapp/copyright
```
Nun muss man die Datei changelog mit folgendem Inhalt befüllen:
```
PlieschneggerVanessa-guiapp (1.0~1) stable; urgency=low

  * creating debian package

  -- Vanessa Plieschnegger <plivac17@htl-kaindorf.at>  Mon, 27 Apr 2020 15:00:00 +0100
```
Jetzt muss man die Datei copyright noch mit folgendem Inhalt befüllen:
```
Format: http://www.debian.org/doc/packaging-manuals/copyright-format/1.0/
Upstream-Name: PlieschneggerVanessa-guiapp

Files: * Copyright: 2020 Vanessa Plieschnegger <plivac17@htl-kaindorf.at>
License: GPL-3+ License: GPL-3+

 This program is ... 
 ...
 On Debian systems, the complete text of the GNU Lesser General
 Public License version 3 can be found in
 "/usr/share/common-licenses/LGPL-
```

### Paketgröße in DEBIAN control korrigieren
Um die Paketgröße der DEBIAN/control Datei zu korrigieren muss man folgende Befehle ausführen:
```
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all$ du -sb usr
17847 usr
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all$ du -s usr
20 usr
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all$ nano DEBIAN/control
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all$ cat DEBIAN/control
Packahe: PlieschneggerVanessa-guiapp
...
Installed-Size: 20
...
```

### Paket erzeugen
Um ein Paket zu erzeugen mmuss man die folgenden Befehle ausführen:
```
user@host:~/PlieschneggerVanessa-guiapp_1.0~1_all$ sudo -i
root@host:~# rsync -aP /home/vani/PlieschneggerVanessa-guiapp_1.0_all ./
root@host:~# chown -R root:root PlieschneggerVanessa-guiapp_1.0_all
root@host:~# dpkg --build PlieschneggerVanessa-guiapp_1.0_all
dpkg-deb: Paket »PlieschneggerVanessa-guiapp« wird in »PlieschnggerVanessa-guiapp_1.0~1_all.deb« gebaut.
root@host:~# ls -l *.deb
-rw-r--r-- 1 root root 3216 Apr 27 15:20 PlieschneggerVanessa-guiapp_1.0~1_all.deb
root@host:~#
```

### Paket installieren
Um nun endlich das Paket installieren zu können, muss man folgenden Befehl ausführen:
```
root@host:~# dpkg --install PlieschneggerVanessa-guiapp_1.0_all.deb
(Lese Datenbank ... 250962 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von PlieschneggerVanessa-guiapp_1.0~1_all.deb ...
Entpacken von PlieschneggerVanessa-guiapp (1.0~1) über (1.0~1) ...
 [INFO] PlieschneggerVanessa-guiapp (postrm) -> /var/lib/dpkg/info/PlieschneggerVanessa-guiapp.postrm upgrade
PlieschneggerVanessa-guiapp (1.0~1) wird eingerichtet ...
 [INFO] sx-guiapp (postinst) -> /var/lib/dpkg/info/sx-guiapp.postinst configure
```
Wenn dies ohne Probleme funktioniert hat, ist ihr Paket nun erfolgreich installiert.
