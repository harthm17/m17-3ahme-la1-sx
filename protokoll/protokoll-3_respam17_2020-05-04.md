# Protokoll 3 Labor-SX 2020
--------------------------------
## Installieren von Ubuntu (Version 20.04) mittels virtuellen Maschine
* **Datum:** 04.05.2020
* **Fehlend:** --
* **Erstellt von:** Resch Paul
* **Übungsort:** Wegen Corona im Home-Office
-----------------------------------
### Inhaltsangabe
1) [Allgemeines](#allgemeines)
1) [Virtuelle Maschine](#download-der-virtuellen-maschine)
1) [Extension Pack](#installieren-des-oracle-vm-virtualbox-extension-pack)
1) [Ubuntu](#ubuntu)
1) [Erstellen der Viruellen Maschine](#erstellen-der-viruellen-maschine)
    * [Erzeugen](#erzeugung-der-vm)
1) [Guest Additions](#installieren-der-virtualbox-guest-additions)
1) [Gemeinsamer Ordner](#gemeinsamer-ordner)
    * [Problembehandlung](#problem-welches-bei-mir-aufgetreten-ist)
1) [HTL-Paket](#htl-paket)

-----------------------------------
### Allgemeines
In unserem Fall, brauchen wir für die Laboraufgaben Ubuntu. Da kaum ein Schüler mit diesem System arbeitet benötigen wir zunächst eine virtuelle Maschine.In der VM kann man dann Ubuntu installieren uns sozusagen zeitgleich mit einem anderen System (Windows, macOS, usw. ) verwenden. Das "Haupsystem" wird Host System genannt.

Laut [Wikipedia](https://de.wikipedia.org/wiki/Virtuelle_Maschine):
> Als virtuelle Maschine (VM) wird in der Informatik die Software-technische Kapselung eines Rechnersystems innerhalb eines lauffähigen Rechnersystems bezeichnet. Die virtuelle Maschine bildet die Rechnerarchitektur eines real in Hardware existierenden oder eines hypothetischen Rechners nach.

Man kann Ubuntu auch ohne virtuelle Maschine installieren, jedoch überschreibt man somit sein aktuelles Betriebssystem.

--------------------------------------------------------
### Download der virtuellen Maschine
Das Installieren der [Oracle VM VirtualBox](https://www.oracle.com/virtualization/technologies/vm/downloads/virtualbox-downloads.html) sollte normalerweise kein Problem darstellen. Einfach das aktuelle Betriebssystem auswählen und den nächsten Anweisungen folgen.

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

### Installieren der VirtualBox Guest Additions 
Wie auch schon das Oracle [VM VirtualBox Extension Pack](#installieren-des-oracle-vm-virtualbox-extension-pack), sollte dies automatisch schon passiert sein.

Falls das trotzdem nicht passiert ist die Schritte Anschließend befolgen:
* VM starten
* In der Menüleiste auf die Kategorie *Geräte* klicken
* Auf *Gasterweiterung einlegen...* klicken
* Den Anweisungen folgen

-----------------------------
### Gemeinsamer Ordner
#### Verzeichniss zwischen Gastsystem und Host System
Zunächst einen Ordner am Host System erstellen und geeignet benannt. Dieser Ordner wird für den Datenaustausch zwischen dem Host- und dem Gastsystem sorgen.

Für die einbindung des Ordners:
* In der Menüleiste auf die Kategorie *Geräte* klicken
* Den Punkt *Gemeinsame Ordner* klicken
* Auf das Symbol mit *grünem Plus* klicken
    * Ordnerpfad angaben
    * Namen wählen (empfohlen: selben Namen wie am Host System)
    * Punkte *Automatisch einbinden* und *Permanent erzeugen* auswählen
* Gastsystem neu Starten
* Checken ob der Ordner vorhanden ist

#### Problem welches bei mir Aufgetreten ist
Keine Zugriffsrechte auf den Gemeinsamen Ordner.

Lösung des Problemes:

In der Konsole (siehe dazu: [Protokoll 2](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/respam17/protokoll/protokoll-2_respam17_2020-01-13.md#konsole) oder [Wikipedia](https://de.wikipedia.org/wiki/Unix-Shell)) den aktuellen Benutzer zur Gruppe, welche den Ordner besitzt hinzufügen.

Hierfür folgendes Kommando eingeben:
* sudo usermod -aG [Gruppenname] [Aktueller-Beutzer] 
in diesem Fall also:
* sudo usermod -aG vboxsf '....'

----------------------------------
### HTL-Paket
Hierfür die Konsole aufrufen und [DIESE](http://www.htl-mechatronik.at/ubuntu-htl/readme) Angabe befolgen. Es sollte alles automatisch funktionieren.

-------------------------------------

> Kurz vor der Installation des HTL-Paketes war die Unterrichtseinheit zu Ende.

> Weitere Aufgaben sind vom Angabenzettel abzulesen.

---------------------------------------
