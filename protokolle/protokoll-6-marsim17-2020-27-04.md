# Protokoll LA1/SX 3AHME (2019/20)

* **Thema:** Debian Paket erstellen
* **Datum:** 27.04.2020
* **Gefehlt:** -
* **Erstellt von:** Marcher Simon
* **Protokoll letzte Einheit:** [Protokoll 20.04.2020](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/marsim17/protokolle/protokoll-5-marsim17-2020-27-04.md)
---------

## GUI App mit Java
Als erstes wurde eine Swing GUI mit Java erstellt. Es wurde ein einfacher Button verwendet, in dessen Handler-Methode ein Message-Dialog aufgerufen wurde. Die GUI erhielt auch noch einen Titel, eine minimale Größe und wurde in der Mitte des Bildschirms gestartet. Da der Hauptfokus dieses Protokolls auf der Paketerstellung liegen soll, sind weitere Informationen in [diesem Video](https://cloud.htl-mechatronik.at/index.php/s/AlyXs7YglQDLZSP) und mein Netbeans Projekt [hier](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/tree/1727ebfdd5a4c0e8ad4912b7c08a02dc55657d4b/protokolle/einheit6/guiApp) zu finden.

## Erstellen des Paket-Ordners

Jedes Debian Paket startet einem Ordner, der wie folgt benannt sein sollte: `<Programmname>_<Version>_<Architektur>`, also in meinem Beispiel `marsim17-guiapp_1.0~1_all`. Bei der Installation wird das gesamte Paket, bis auf den Unterordner DEBIAN auf `/` kopiert. Will man also, dass sich eine Datei am Ende in `/usr/share/` befindet, muss man sie im Paketordner unter `/usr/share/` abspeichern. Alle Datein in DEBIAN beinhalten Informationen zum Paket, Installation und Deinstallation.

### DEBIAN/control
Diese Datei beinhaltet die Informationen zum Paket. In meinenm Fall sieht sie so aus:
```
Package: marsim17-guiapp
Version: 1.0~1
Architecture: all
Depends: default-jre (>=2:1.11)
Installed-Size: 56
Maintainer: Marcher simon <marsim17@htl-kaindorf.ac.at>
Description: My first Java GUI Application
```

Der Großteil davon ist selbsterklärend. `Depends` gibt an, welche anderen Programme benötigt werden, in dem Fall `default-jre` Version 2:1.11 oder größer.

### DEBIAN/postinst und DEBIAN/postrm
Diese beiden Dateien sind [Shell-Skripte](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/1727ebfdd5a4c0e8ad4912b7c08a02dc55657d4b/protokolle/protokoll-5-marsim17-2020-20-04.md), die ausgeführt werden, nachdem das Programm installiert oder deinstalliert wurde. In meinem Fall führten sie folgenden Befehl aus:

postinst: `printf '%b' "\033[32;1m [INFO] marsim17-guiapp (postinst) -> $0 $1 \033[0m\n"`

postrm: `printf '%b' "\033[32;1m [INFO] marsim17-guiapp (postrm) -> $0 $1 \033[0m\n"`

### Programm einfügen
Das eigentliche Programm muss jetzt im Paketordner so angelegt werden, als wäre es der root des Systems. Die `marsim17-guiapp.jar` Datei, sowie `icon.png` kommen nach `usr/share/marsim17-guiapp/`, die `marsim17-guiapp.desktop` Datei kommt nach `usr/share/applications/`. Die Desktop-Datei ist der Starter des Programms, der angibt, wie das Programm heißt, wie es ausgeführt wird, welches Icon verwendet wird, etc. Meine Datei sieht folgendermaßen aus:
```
[Desktop Entry]
Name=marsim17-guiapp
GenericName=marsim17 Java Gui Application
GenericName[de]=marsim17 Java Gui Applikation
Comment=My first Java GUI Application for Ubuntu
Exec=java -jar /usr/share/marsim17-guiapp/marsim17-guiApp.jar
Icon=/usr/share/marsim17-guiapp/icon.png
Terminal=false
Type=Application
StartupNotify=false
```

Das Icon musste selbst erstellt werden, wobei ich mich für das Swift-Logo mit einer Größe von 64x64 entschied.

### Paketdokumentation
Die Paketdokumentation, wie sie auf einer DEBIAN-Distribution für jedes Paket vorhanden ist, befindet sich in `usr/share/doc/marsim17-guiapp/`. Sie besteht in meinem Fall aus den Dateien `changelog` und `copyright`.

`changelog`
```
marsim17-guiapp (1.0~1) stable; urgency=low

  * creating debian package

  -- Marcher Simon <marsim17@htl-kaindorf.ac.at>  Mon, 27 Apr 2020 15:11:32 +0100
```
`copyright`
```
Format: http://www.debian.org/doc/packaging-manuals/copyright-format/1.0/
Upstream-Name: marsim17-guiapp

Files: * Copyright: 2020 Marcher Simon <marsim17@htl-kaindorf.at>
License: GPL-3+ License: GPL-3+

 This program is ... 
 ...
 On Debian systems, the complete text of the GNU Lesser General
 Public License version 3 can be found in
 "/usr/share/common-licenses/LGPL-3".
```
### Paketgröße korrigieren
Da das Paket jetz vollständig ist, muss die Paketgröße in `DEBIAN/control` angepasst werden. Mit `du -s usr` wird die Größe des Ordners `usr/` in KiB ausgegeben. `du` steht hierbei für Disk Usage.

## Paket erzeugen
Bevor das Paket gepackt wird, muss noch der Eigentümer geändert werden. Das passiert, indem man als root mit `sudo -i` einsteigt und mit `rsync -aP <Pfad-zum-Paket>/marsim17-guiapp_1.0~1_all ./` eine Kopie des Pakets macht. Mit `chown -R marsim17-guiapp_1.0~1_all` wird schließlich der Eigentümer geändert. Zur Sicherheit kann sich als root wieder mit `exit` ausloggen. 

Mit `sudo dpkg --build marsim17-guiapp_1.0~1_all` wird das Paket gepackt und die Dabei `marsim17-guiapp_1.0~1_all.deb` sollte jetzt existieren. 

## Paket installieren
Mit `sudo dpkg --install marsim17-guiapp_1.0~1_all.deb` wird das Paket installiert. Jetzt sollte sich das Programm per Starter, wie jedes andere Programm starten lassen. 
