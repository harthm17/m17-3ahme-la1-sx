# Protokoll LAB/Sx 3.AHME (2020)

* **Thema:** Installation von Ubuntu 18.04 LTS + Software in einer virtuellen Maschine
* **Datum:** 23.03.2020
* **Gefehlt:** -
* **Esrtellt von:** Franz Lieleg (liefrm)
* **Protokoll der letzten Einheit:**
* **Protokoll der nächsten Einheit:**

--------------------------------------------------------------------------------------------------------
## Inhaltsverzeichnis:

1. [Installation von Virtualbox](#installatio-von-virtualbox)
1. [Installation von Oracle VM VirtualBox Extension Pack](#installation-von-oracle-vm-virtualbox-extension-pack)
1. [Erstellen und einrichten einer virtuellen Maschine](#erstellen-und-einrichten-einer-virtuellen-maschine)
1. [Installation von Ubuntu 18.04 LTS in der virtuallen Maschine](#installetion-von-ubuntu-18.04-lts-in-der-virtuallen-maschine)
1. [Installation von Virtualbox Guest Additions in Ubuntu](#installation-von-virtualbox-guest-additions-in-ubuntu)
1. [Ein Verzeichnis zwischen dem Gastsystem und dem virtuellen System erstellen](#ein-verzeichnis-zwischen-dem-gastsystem-und-dem-virtuellen-system-erstellen)
1. [Installation des HTL Paketes](#installation-des-htl-paketes)
1. [Konfiguration des Lesezeichens in Firefox/Chrome](#konfiguration-des-lesezeichens-in-firefox/chrome)
1. [Resume](#resume)

-------------------------------------------------------------------------------------------------------
## Installation von Virtualbox
Mit dem Link https://www.virtualbox.org/wiki/Downloads wird die Seite für die Installation der **VirtualBox** im Internet aufgerufen.

### Packet aussuchen
Die Virtualbox für das jeweillige am Computer laufende Betriebssystem herunterladen, in meinem Fall war es für Windows.
![](https://cdn.discordapp.com/attachments/691664570208616518/692317087728664606/unknown.png)

-----------------------------------------------------------------------------------------------------------
## Installation von Oracle VM VirtualBox Extension Pack
Mit dem Link https://download.virtualbox.org/virtualbox/6.1.4/Oracle_VM_VirtualBox_Extension_Pack-6.1.4.vbox-extpack gelingt man auf die Seite für die Inastallation von **Oracle VirtualBox Extension Pack**, danach wird mit **"Öffnen"** der Seite die VirtualBox, sprich, der Oracle VirtualBox Manager, aufgerufen. Nur die Installation muss ausgeführt werden. Alles funktioniert bis zum nächsten Punkt Automatisch!
![](https://cdn.discordapp.com/attachments/691664570208616518/692322046234853436/unknown.png)
Diese Grafik unterscheidet sich in gewissen unbeachtlichen Punkten mit der zuerst erscheinenden. In diesem Bild ist Ubuntu bereits in der Virtualbox Installiert.

---------------------------------------------------------------------------------------------------------------
## Erstellen und einrichten einer virtuellen Maschine
**Währendessen Punkt 3 hier angeführt wird, kann Punkt 4  schon ausgeführt werden. Punkt 4 wird dennoch extra beschrieben!**

### Einrichten der Virtualbox
Im **Oracle VirtualBox Manager** wird als aller erstes eine neue virtuelle Maschine erstellt, durch Drücken des Symboles **"Neu"**, dass sich oben mittig im Programmfenster befindet.

![](https://cdn.discordapp.com/attachments/691664570208616518/692330649960448020/unknown.png)

Danach erscheint ein nächstes Fenster, die nächsten Tätigkeiten werden nur in diesem Fenster ausgeführt! 
* **Ordner:** gewünschten Namen eingeben
* **Dateipfad:** gewünschten Dateipfad, wo die Dateien gespeichert werden, auswählen
* **Typ:** Linux auswählen
* **Version:** Ubuntu (64-Bit) auswählen
![](https://media.discordapp.net/attachments/691664570208616518/692334047136841748/unknown.png?width=1443&height=617)

Danach auf **"Weiter"** drücken!

**Nächster Schritt:** Arbeitsspeicher zuweisen. Es werden mindestens 4GiB empfohlen.
![](https://media.discordapp.net/attachments/691664570208616518/692336097077755944/unknown.png)

Danach auf **"Weiter"** drücken!

**Nächster Schritt:** Virtuelle Festplatte zuweisen. Es werden mindestens 50GiB empfohlen.
![](https://media.discordapp.net/attachments/691664570208616518/692339161868402738/unknown.png)

Danach auf **"Erzeugen"** drücken!



**Ein Wichtiger Punkt:** Unter (**"Ändern"->"Allgemein"->"Erweitert"**) soltte folgendes festgelegt werden:
* **Gemeinsame Zwischenablage:** bidirektional
* **Drag´n´Drop:** bidirektional
![](https://media.discordapp.net/attachments/691664570208616518/692342307244212276/unknown.png)



**Nächster Schritt:** Die Ubunto.iso Datei, die schon heruntergeladen wurde, in die Virtuelle Maschine einfügen. Dazu geht man unter **"Ändern"->"Massenspeicher"**. Den Pfad **"Controller: IDE"** auswählen und auf das Symbol(**"Blaue CD"**) klicken, wiederrum dann die Ubuntu.iso Datei auswählen.
![](https://media.discordapp.net/attachments/691664570208616518/692378909374939165/unknown.png)
