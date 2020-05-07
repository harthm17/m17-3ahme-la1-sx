# Protokoll-3 LABOR/SX 3AHME (2019/20)

---------------------------------------------------------------------------------------------

* **Thema:** Installation von Ubuntu 18.04 LTS + Software in einer virtuellen Maschine
* **Datum:** 04.05.2020
* **Gefehlt:** -
* **Erstellt von:** Riegelnegg Lukas (rielum17)
* **Protokoll der letzten Einheit:** [Protokoll 2](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/rielum17/Protokoll/protokoll-2_rielum17_2020-01-13.md)
----------------------------------------------------------------------------------------------

## Inhaltsverzeichnis  

1. [Download von Virtualbox](#download-von-virtualbox)
1) [Extension Pack](#installieren-des-oracle-vm-virtualbox-extension-pack)
1) [Ubuntu](#ubuntu)
1) [Erstellen der Viruellen Maschine](#erstellen-der-viruellen-maschine)
    * [Erzeugen](#erzeugung-der-vm)
1) [HTL-Paket](#htl-paket)
-------------------------------------------------------------------------------------

Das benutzte Betriebssystem war Ubunto.

### Download von Virtualbox

Unter folgendem Link kann man Virtualbox auf seinem jeweiligen Betriebssystem herunterladen. Bei Linux muss alerdings die Kernversion übereinpassen.
ich hatte probleme beim download da ich derzeit noch eine etwas ältere Ubunto version habe(16.04). Der download wollte bei imr nicht starten.

[Virtualbox Download](https://www.virtualbox.org/wiki/Downloads)

Anschliesend habe ich mich im Internet eingelesse wie ich auf meine Kernversion eine VirtualBox über den Terminal runterladen kann was auch geklappt hat. 

-------------------------------------------------------------------------------------------------------------------

### Oracle VM VirtualBox Extension Pack installieren
Dannach muss das Oracle VM VirtualBox Extension Pack heruntergeladen werden. Dies wird dann auch automatisch installiert. Um das Pack herunterzuladen, klicken Sie auf [Extension Pack](https://download.virtualbox.org/virtualbox/6.1.4/Oracle_VM_VirtualBox_Extension_Pack-6.1.4.vbox-extpack)

-----------------------------------------------------------------------------------------------------------------

### Ubuntu
Anschließend die ISO-Datei von [Ubuntu 20.04](https://ubuntu.com/download/desktop) downloaden. Zu beachtende ist, dass die Desktopversion und nicht die Version für Server heruntergeladen wird, unteranderm ist es  auch wichtig sich seinen Dateipfad zu merken, weil man diesen später noch benötigt.

-------------------------------------------------------------------------------------------------------------

### Erstellen der Viruellen Maschine

Man muss folgendes unbedijngt beachten, damit man Ubuntu als Gastsystem in der VirtualBox verwenden kann.

Im BIOS muss unbedingt die Hardwarevisualisierung aktiviert sein, da es sonst zu Problemen kommt. Weiters soll laut unserer Angabe das Gastsystem einen 4 GiB RAM und eine Festplatte mit zumindest 50 GiB haben. Ich habe dem ganzen 6 GiB Ram und 60 GiB speicher auf der Festplatte gegeben.

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

Wenn man erneut auf "Ändern" geht und dann auf "Gemeinsamer Ordner" geht, kann man einen Gemeinsamen Ordner erstellen. Mit diesem kann man zwischen dem Gastsystem und dem virtuellen System ein Verzeichnis teilen.
![](https://cdn.discordapp.com/attachments/692432976503373854/692693823565856809/bild6.PNG)

------------------------------------------------------------------------------

### HTL-Paket
Hierfür die Konsole aufrufen und [DIESE](http://www.htl-mechatronik.at/ubuntu-htl/readme) Angabe befolgen. Es sollte alles automatisch funktionieren.

------------------------------------------------------------------------

> Kurz vor der Installation des HTL-Paketes war die Unterrichtseinheit zu Ende.

> Weitere Aufgaben sind vom Angabenzettel abzulesen.
