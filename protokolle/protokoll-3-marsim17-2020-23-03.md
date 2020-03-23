# Protokoll LA1/SX 3AHME (2019/20)

* **Thema:** Installation von Ubuntu 18.04 LTS + Software in einer virtuellen Maschine
* **Datum:** 23.03.2020
* **Gefehlt:** -
* **Erstellt von:** Marcher Simon
* **Protokoll letzte Einheit:** [Protokoll 02.12.2019](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/marsim17/protokolle/protokoll-2-marsim17-2019-02-12.md)
---------
## Inhaltsverzeichnis

[Installieren der Software](#installieren-der-software)

[Installieren der VirtualBox](#installieren-der-virtualbox)

[Installieren des Extention Packs](#installieren-des-extention-packs)

[Alle Features der VirtualBox freischalten](#alle-features-freischalten)

[Aktivieren der Hardwarevisualisierung](#aktivieren-der-hardwarevisualisierung)

[Herunterladen des Ubuntu 18.04 Images](#herunterladen-des-ubuntu-18.04-images)

[Erstellen der virtuellen Maschine](#erstellen-der-virtuellen-maschine)

[Installieren der VirtualBox Guest Additions](#installieren-der-virtualbox-guest-additions)

[Verzeichnis teilen](#verzeichnis-teilen)

[Installieren des HTL-Packetes](#installieren-des-htl-packetes)

[Lesezeichen in Firefox und Chrome wiederherstellen]

## Installieren der Software

Das benutzte Betriebssystem war [Manjaro](https://wiki.manjaro.org/index.php?title=Main_Page) KDE, Kernel Version: 5.4.24-1-MANJARO

### Installieren der VirtualBox

Um VirtualBox zu installieren braucht man die beiden Packages `virtualbox` und `linux*-virtualbox-host-modules`, wobei die Nummer beim zweiten mit der Kernelversion zusammenpassen muss.
Die Kernelversion findet man mit `mhwd-kernel -li` herausfinden, in meinem Fall linux54. 
Die Packages werden mit `sudo pacman -Syu virtualbox linux54-virtualbox-host-modules` installiert.
Nach dem Installieren muss das System entweder neu gestartet werden oder mit `sudo vboxreload` initialisiert werden um direkt benutzt werden zu können.

### Installieren des Extention Packs

Das Extention Pack ist im [AUR](https://wiki.manjaro.org/index.php?title=Arch_User_Repository) verfügbar und kann mit `pamac build virtualbox-ext-oracle` installiert werden.

## Alle Features der VirtualBox freischalten

Um die volle Funktionalität der VirtualBox, wie das Verwenden von USB-Schnittstellen, zu nutzen, muss man seinen Benutzer zur Gruppe vboxusers hinzufügen.
Das ist mit `sudo gpasswd -a $USER vboxusers` möglich. `$USER` wird automatisch mit dem Benutzernamen ausgetauscht. Diese Änderung tritt jedoch erst nach einamligen Ausloggen in Kraft.

## Aktivieren der Hardvarevisualisierung

Mit dem Befehl `systemctl reboot --firmware-setup` kommt man direkt ins BIOS, wo man unter `Advanced` die Hardwarevisualisierung aktivieren kann.

## Herunterladen des Ubuntu 18.04 Images

Um die ISO-Datei von Ubuntu 18.04 herunterzuladen muss man im gewünschten Arbeitsverzeichnis `wget http://mirrors.rit.edu/ubuntu-releases/18.04.4/ubuntu-18.04.4-desktop-amd64.iso` ausführen. Die Datei ist in etwa 2GiB groß, wodurch der Download etwas Zeit in Anspruch nehmen könnnte.

## Erstellen der virtuellen Maschine

Es wurde eine Box mit 2 CPU-Kernen, 4GiB RAM und 50GiB Festplattenspeicher erstellt. Als optisches Laufwerk wurde die vorher heruntergeladene Datei ausgewählt.

## Installieren der VirtualBox Guest Additions

Unter Ubuntu 18.04 ist dieses Packet bereits automatisch installiert und aktiviert. 

## Verzeichnis teilen

In den Einstellungen der virtuellen Maschine kann man unter "Geräte" einen beliebigen Ordner auf dem Wirtsystem auswählen. Im Hostsystem wird danach automatisch ein Ordner erstellt. Diese beiden sind immer synchronisiert, wodurch Daten zwischen den Systemen ausgetauscht werden können.

## Installieren des HTL-Packetes

Zum Installieren des HTL Packetes geht man folgendermaßen vor: [htl-mechatronik.at](http://www.htl-mechatronik.at/ubuntu-htl/readme)

## Lesezeichen in Firefox und Chrome wiederherstellen

Da sich die Anleitung zu diesem Schritt von Version zu Version ändern kannn habe ich auf die aktuelle Anleitung von [Firefox](https://support.mozilla.org/de/kb/Lesezeichen-sichern-und-wiederherstellen) und [Chrome](https://support.google.com/chrome/answer/96816?hl=de) verwiesen.
