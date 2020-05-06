# Protokoll 3 Labor-SX 2020
--------------------------------
## Installieren von Ubuntu (Version 20.04) mittels virtuellen Maschine
* **Datum:** 04.05.2020
* **Fehlend:** --
* **Erstellt von:** Resch Paul
* **Übungsort:** Wegen Corona im Home-Office
-----------------------------------
### Allgemeines
In unserem Fall, brauchen wir für die Laboraufgaben Ubuntu. Da kaum ein Schüler mit diesem System arbeitet benötigen wir zunächst eine virtuelle Maschine.In der VM kann man dann Ubuntu installieren uns sozusagen zeitgleich mit einem anderen System (Windows, macOS, usw. ) verwenden. Das "Haupsystem" wird Host-System genannt.

Laut [Wikipedia](https://de.wikipedia.org/wiki/Virtuelle_Maschine):
> Als virtuelle Maschine (VM) wird in der Informatik die Software-technische Kapselung eines Rechnersystems innerhalb eines lauffähigen Rechnersystems bezeichnet. Die virtuelle Maschine bildet die Rechnerarchitektur eines real in Hardware existierenden oder eines hypothetischen Rechners nach.

Man kann Ubuntu auch ohne virtuelle Maschine installieren, jedoch überschreibt man somit sein aktuelles Betriebssystem.

--------------------------------------------------------
### Download der virtuellen Maschine
Das Installieren der [Oracle VM VirtualBox](https://www.oracle.com/virtualization/technologies/vm/downloads/virtualbox-downloads.html) sollte normalerweise kein Problem darstellen. Einfach das aktuelle Betriebssystem auswählen und den nächten Anweisungen folgen.

------------------------------------------------

### Installieren des Oracle VM VirtualBox Extension Pack
Nachdem die VirtualBox installiert wurde, soll man das [Extension Pack](https://www.oracle.com/virtualization/technologies/vm/downloads/virtualbox-downloads.html#extpack) installieren. Dieses sollte automatisch schon passiert sein.

-------------------------------------------------
### Ubuntu
Anschließend die ISO-Datei von [Ubuntu 20.04](https://ubuntu.com/download/desktop) downloaden. Das einzig zu beachtende ist, dass die Desktopversion und nicht die Version für Server heruntergeladen wird. Außerdem ist es wichtig sich den Dateipfad zu merken, da man diesen später benötigt.

-----------------------------------------
### Erstellen der Viruellen Maschine
Um Ubuntu als Gastsystem in der VirtualBox verwenden zu können, muss man folgendes unbedingt Beachten.

Im BIOS muss unbedingt die Hardwarevisualisierung aktiviert sein, da es sonst zu Problemen kommt. Weiters soll laut unserer Angabe das Gastsystem einen 4 GiB RAM und eine Festplatte mit zumindest 50 GiB haben.

#### Erzeugung der VM

1) Um starten zu können auf *Neu* klicken
1) Mehr oder weniger Beliebigen Namen auswählen
1) Ordner der VM auswählen
1) Typ vom Betriebssystem wählen (in unserem Fall: *Linux*)
1) Version auswählen (in unserem Fall: *Ubuntu 64bit*)
1) Hauptspeichergröße bzw. RAM wählen 
1) Den Punkt *Festpaltte erzeugen* wählen und auf *Erzeugen* klicken
1) *VDI (VirtualBox Disk Image)* wählen 
1) Festplatte soll *feste Größe* haben
1) Festplattengröße festlegen
1) Nur noch die *ISO-Datei von Ubuntu* auswählen

Empfohlen wird noch folgendes einzustellen:
* Einstellungen -> Allgemein -> Erweitert
* Gemeinsame Zwischenablage: *bidirektional*
* Drag'n'Drop: *bidirektional*

Nun hat man ein Lauffähiges Betriebssystem in der VirtualBox

----------------------------------

### Installieren der Virtualbox Guest Additions 
Wie auch schon das Oracle [VM VirtualBox Extension Pack](#installieren-des-oracle-vm-virtualbox-extension-pack), sollte dies automatisch schon passiert sein.


















