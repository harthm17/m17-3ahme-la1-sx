# Protokoll LA1/SX 3AHME (2019/20)

* **Thema:** Installation von Ubuntu 18.04 LTS + Software in einer virtuellen Maschine
* **Datum:** 23.03.2020
* **Gefehlt:** -
* **Erstellt von:** Marcher Simon
* **Protokoll letzte Einheit:** [Protokoll 02.12.2019](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/marsim17/protokolle/protokoll-2-marsim17-2019-02-12.md)
---------
## Inhaltsverzeichnis

## Aktivieren der ...?

##Installieren der Software

Das benutzte Betriebssystem war [Manjaro](https://wiki.manjaro.org/index.php?title=Main_Page) KDE, Kernel Version: 5.4.24-1-MANJARO

### Installieren der VirtualBox

Um VirtualBox zu installieren braucht man die beiden Packages `virtualbox` und `linux*-virtualbox-host-modules`, wobei die Nummer beim zweiten mit der Kernelversion zusammenpassen muss.
Die Kernelversion findet man mit `mhwd-kernel -li` herausfinden, in meinem Fall linux54. 
Die Packages werden mit `sudo pacman -Syu virtualbox linux54-virtualbox-host-modules` installiert.

### Installieren des Extention Packs

Das Extention Pack ist im [AUR](https://wiki.manjaro.org/index.php?title=Arch_User_Repository) verfügbar und kann mit `pamac build virtualbox-ext-oracle` installiert werden.

## Alle Features der VirtualBox freischalten

Um die volle Funktionalität der VirtualBox, wie das Verwenden von USB-Schnittstellen, zu nutzen, muss man seinen Benutzer zur Gruppe vboxusers hinzufügen.
Das ist mit `sudo gpasswd -a $USER vboxusers` möglich. `$USER` wird automatisch mit dem Benutzernamen ausgetauscht. Diese Änderung tritt jedoch erst nach einamligen Ausloggen in Kraft.
