# Laborprotokoll 18.05.2020 Pfanner


* **Thema:** Erstellen eines Debian-Paketes
* **Datum:** 18.05.2020
* **Gefehlt:** -
* **Erstellt von:** Pfanner Jan

## Inhaltsverzeichnis
* [GUI-App mit Java](#gui-app-mit-java)
* [Anlegen der nötigen Dateien und Verzeichnisse](#anlegen-der-nötigen-dateien-und-verzeichnisse)
* [Erstellen und Installieren des Debian-Paketes](#erstellen-und-installieren-des-debian-paketes)

## GUI-App mit Java
Alle `hervorgehobenen` Stellen in diesem Absatz beziehen sich auf Java-Befehle, die in den Quellcode einzufügen sind.

Als erster Schritt diente die Erstellung einer App mit grafischer Oberfläche in der simplen Form eines einzigen Knopfes, der bei Betätigung eine Textbox ausgibt.

Hierfür kann man unter Ubuntu NetBeans nutzen, indem man in einem Java-Projekt (muss keine main-Klasse haben) eine besondere Klasse anlegt, genannt **JFrame Form**. Hiermit kann man leicht grafische Oberflächen erzeugen. Der Reiter *Source* beinhaltet den Quellcode, unter *Design* kann man das Aussehen der Ausgabe anpassen. Mit Rechtsklick auf JFrame im Navigator und Auswahl von *Set Layout* kann man das Layout festlegen, in unserem Fall auf Flow Layout. Per Drag-and-Drop kann nun der Knopf (button) in das GUI eingefügt und gleich benannt werden. Der Nam des button-Objektes im Programm selbst ist unter *Change variable name* einstellbar. Ein Blick in den Quellcode verrät, dass das Objekt Knopf angelegt wurde. Möchte man dem GUI einen Titel geben, geht dies mit `setTitle("Titel hier")`. Ort und Größe können mit `setLocationRelativeTo()` (die Position null ist in der Bildschirmmitte) und `setMinimumSize(Anzahl Pixel LR, Anzahl Pixel OU)`. Möchte man mit dem Knopf interagieren, reicht ein Doppelklick auf denselben unter *Design* zum Anlegen einer Methode, die beim Drücken aktiv wird. Der Befehl ```JOptionPane.showmessageDialog(this, "Knopf gedrückt", "Nachricht", JOptionPane.INFORMATION_MESSAGE)``` in dieser Methode sorgt dafür, dass beim Drücken des Knopfes die Nachricht *Knopf gedrückt* in einem info-panel ausgegeben wird. Ist das Programm beim Ausführen nicht mehr aktuell, kann man mit Clean&Build sicherstellen, dass alle Änderungen übernommen werden. 

Damit ist die GUI fertig und kann als .jar-Datei im Projektordner im Ordner **dist** gefunden werden.

## Anlegen der nötigen Dateien und Verzeichnisse
Alle `hervorgehobenen` Stellen in diesem Absatz beziehen sich auf Befehle, die in der Ubuntu-Shell (Terminal) auszuführen sind. Alle Instanzen von *pfajam17* sind durch das eigene Kürzel zu ersetzen.

Im /home/user-Verzeichnis den Ordner für das Debian-Paket mit `mkdir pfajam17-guiapp_1.0~1_all` anlegen (der Tabulator hilft ungemein beim Eingeben). Mit `cd pfajam-guiapp_1.0~1_all` in das Verzeichnis wechseln. Die Unterstriche teilen den Namen in drei Teile: Programmname_Version_Architektur. 1.0~1 bedeutet, dass es die Version 1.0 mit Unterversion 1 des Pakets ist. All bedeutet, dass das Paket dank Java auf jeder Architektur lauffähig ist. 

Hier erstellen wir nun den Unterordner DEBIAN mit `mkdir DEBIAN`, danach `cd DEBIAN`. Mithilfe des Texteditors nano legen wir die Datei control an - `nano control`. Dies ist die sogenannte Steuerdatei, die folgende Informationen benötigt:
```
Package: pfajam17-guiapp
Architecture: all
Depends: default-jre (>=2:1.11)
Installed-Size: 1000
Maintainer: Jan Pfanner
Description: My first Java GUI Application
Version: 1.0
```
Der Eintrag **Version** wird in der Angabe nicht vorgegeben, ist aber notwendig. Die Installed-Size ist noch nicht bekannt und daher vorsichtshalber auf "sicher groß genug" festgelegt.

Im Ordner DEBIAN kann man bei Bedarf Skriptdateien ablegen, die bei Installation/Deinstallation ausgeführt werden. Mit `touch postinst` wird die Datei postinst (post installation - nach der Installation) angelegt, `chmod +x postinst` gibt ihr ausführende Rechte. Mit `nano postinst` kann man nun folgendes einfügen:
```
#!/bin/sh
#set -e
#set -x

printf '%b' "\033[32;1m [INFO] pfajam17-guiapp (postinst) -> $0 $1 \033[0m\n"
```
Die mit # beginnenden Zeilen werden nicht ausgeführt, jedoch legt das #! der ersten Zeile das Programm fest, das zur Ausführung des Skriptes dient, hier die Ubuntu dash-Shell /bin/sh. Der printf-Befehl gibt in grüner Farbe eine Infomeldung aus. Auf die selbe Art kann man das Skript postrm (post remove - nach der Deinstallation) folgendermaßen befüllen:
```
#!/bin/sh
#set -e
#set -x

printf '%b' "\033[32;1m [INFO] pfajam17-guiapp (postrm) -> $0 $1 \033[0m\n"
```
Man beachte: in der Klammer steht hier postrm.

Nun legen wir ein weiteres Verzeichnis im Ordner pfajam17-guiapp_1.0~1_all an. Da wir uns noch im DEBIAN-Ordner befinden, springen wir mit `cd ..` eine Ebene zurück. Nun legen wir mit `mkdir -p usr/share/pfajam17-guiapp` ein neues Verzeichnis an (-p erlaubt, gleich die Unterverzeichnisse share and pfajam17-guiapp mitanzulegen) und kopieren mit `cp .../MyGuiApp/dist/*.jar usr/share/pfajam17-guiapp/` alle .jar-Dateien von dist hierher. 

Das neue Verzeichnis applications - `mkdir usr/share/applications` soll nun eine .desktop-Datei enthalten - `nano pfajam17-guiapp.desktop`. In diese kommt folgender Inhalt:
```
[Desktop Entry]
Name=pfajam17-java-application
GenericName=pfajam17 Java Gui Application
GenericName[de]=pfajam17 Java Gui Applikation
Comment=My first Java GUI Application for Ubuntu
Exec=java -jar /usr/share/pfajam17-guiapp/MyJavaApplication.jar
Icon=/usr/share/pfajam17-guiapp/icon.png
Terminal=false
Type=Application
StartupNotify=false
```
Das icon kann man bei Bedarf selber entwerfen, oder man schnappt sich ein png aus dem Internet. 

Das sind bereits ziemlich viele Dateien und Verzeichnisse, doch ein paar müssen noch erstellt werden. Das Verzeichnis doc soll die Paketinformationen beinhalten, angelegt wird es mit `mkdir -p usr/share/doc/pfajam17-guiapp`. Auch hier kommt -p zum Einsatz, um das Unterverzeichnis pfajam17-guiapp gleich mitzuerstellen. Nun legen wir die Dateien changelog und copyright an, mit `touch usr/share/doc/pfajam17-guiapp/changelog` und `touch usr/share/doc/pfajam17-guiapp/copyright`. In den changelog kommt folgende Information:
```
pfajam17-guiapp (1.0~1) stable; urgency=low

  * created debian package

  -- Jan Pfanner, Mo 18.05.2020 [Erstellungsdatum]
```
um zu zeigen, dass das Debian-package angelegt wurde. Die Datei copyright erhält folgende Information:
```
Format: http://www.debian.org/doc/packaging-manuals/copyright-format/1.0/
Upstream-Name: pfajam17-guiapp

Files: * Copyright: 2020 Jan Pfanner
License: GPL-3+ License: GPL-3+

 This program is ... 
 ...
 On Debian systems, the complete text of the GNU Lesser General
 Public License version 3 can be found in
 "/usr/share/common-licenses/LGPL-3".
```
als Urheberrechtsvereinbarung. 

Nicht vergessen, in der control-Datei ist noch die korrekte Paketgröße ausständig. Diese können wir jetzt herausfinden, indem wir den Befehl `du -sb usr` anwenden. du -s (disc usage) gibt den Gesamtwert der im Speicher verwendeten Bits an, du -sb denselben Wert in KiB und aufgerundet. Dieser Wert ist unter Installed-Size einzutragen. 

## Erstellen und Installieren des Debian-Paketes

Vor dem Paketpacken muss noch der Eigentümer desselben geändert werden. Mit `rsync -aP /home/user/pfajam17-guiapp_1.0_all ./` wird eine Kopie des Pakets angelegt (davor sollte ein `sudo -i` passiert sein). Dann kann man bequem den Eigentümer mittels `chown -R pfajam17-guiapp_1.0_all` ändern. Ist man noch als superuser aktiv, kann man jetzt mit dpkg `--build pfajam17-guiapp_1.0_all` das Paket bauen. Dies erzeugt die Datei *pfajam17-guiapp_1.0~1_all.deb*, überprüfbar mit `ls -l *.deb`. 

Jetzt steht es einem frei, das erstellte und gepackte Paket zu installieren. Dies geht über `dpkg --install pfajam17-guiapp_1.0_all.deb` (Achtung - Tab fügt das .deb am Ende nicht an - selbst machen). Die Ausgabe sieht dann so aus:
```console
root@jan-VirtualBox:~# dpkg --install pfajam17-guiapp_1.0~1_all.deb
(Reading database ... 258865 files and directories currently installed.)
Preparing to unpack pfajam17-guiapp_1.0~1_all.deb ...
Unpacking pfajam17-guiapp (1.0) over (1.0) ...
 [INFO] pfajam17-guiapp (postrm) -> /var/lib/dpkg/info/pfajam17-guiapp.postrm upgrade 
Setting up pfajam17-guiapp (1.0) ...
 [INFO] pfajam17-guiapp (postinst) -> /var/lib/dpkg/info/pfajam17-guiapp.postinst configure 
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu2) ...
Processing triggers for mime-support (3.64ubuntu1) ...
```
Wie man sieht, werden sowohl posrtm als auch postinst ausgegeben. Dies liegt einfach daran, dass das Paket bei erneuter Installation erst gelöscht und dann neu installiert wird. 

Und somit haben wir ein Debian-Paket angelegt und installiert. 
