# Protokoll LAB/Sx 3.AHME (2020)

* **Thema:** Installation von Ubuntu 18.04 LTS + Software in einer virtuellen Maschine
* **Datum:** 23.03.2020
* **Gefehlt:** -
* **Esrtellt von:** Franz Lieleg (liefrm)
* **Protokoll der letzten Einheit:**![2tes Protokol](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/liefrm17/SxLab%20Protokolle/protokoll-2_liefrm17_2019-12-02.md)
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
1. [Konfiguration des Lesezeichens in Firefox/Chrome](#konfiguration-des-lesezeichens-in-firefoxchrome)
1. [Resümee](#resümee)

-------------------------------------------------------------------------------------------------------
**Achtung: So manche Grafiken, die in diesem Protokoll gezeigt  werden, werden sich mit den aufgerufenen Fenstern, die vor der Installation angezeigt werden, sich minimalst unterscheiden!!!**

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

**TIPP:** Falls sich die virtuelle Maschine nicht starten lässt, dann im BIOS des jeweilig verwendeten Computers die Hardwarevisualisierungen aktivieren/umändern. Dieses Problem tritt aber nicht bei jedem Benutzer auf.

-------------------------------------------------------------------------------------------------------------------------
## Installation von Ubuntu 18.04 LTS in der virtuallen Maschine
Mit dem Link https://ubuntu.com/download/desktop/thank-you?version=18.04.4&architecture=amd64 wird die Seite zur Installation der Ubuntu.iso Datei aufgerufen. Um weiterzumachen sofort installieren!

 Die Ubunto.iso Datei, die dann schon heruntergeladen wurde, in die Virtuelle Maschine einfügen. Dazu geht man unter **"Ändern"->"Massenspeicher"**. Den Pfad **"Controller: IDE"** auswählen und auf das Symbol(**"Blaue CD"**) klicken, wiederrum dann die Ubuntu.iso Datei auswählen.
![](https://media.discordapp.net/attachments/691664570208616518/692378909374939165/unknown.png)

Jetzt ist Ubuntu in der virtuellen Maschine Installationsbereit!

-------------------------------------------------------------------------------------------------------------------------------------
## Installation von Virtualbox Guest Additions in Ubuntu
Befindet man sich in der virtuellen Maschine, wählt man: **"Geräte"->Medium mit Gasterweiterung einlegen**, dann die Guest Additions installieren (**VBoxWindowsAdditions.exe**).

![](https://media.discordapp.net/attachments/691664570208616518/692384601942786188/unknown.png)

-----------------------------------------------------------------------------------------------------------------------------------
## Ein Verzeichnis zwischen dem Gastsystem und dem virtuellen System erstellen
* Im Gastsystem Ordener erstellen
* Dann in Oracle VM  VirtualBox Manager auf **"Ändern"->"Gemeinsame Ordner"** auswählen
* Anschließend auf das Symbol (**"Grünes Plus"**) klicken
* Zum Schluss gewünschten Ordener auswählen

![](https://cdn.discordapp.com/attachments/691664570208616518/692387478677487646/unknown.png)

------------------------------------------------------------------------------------------------------------------------------------
## Installation des HTL Paketes
Mit dem Link http://www.htl-mechatronik.at/ubuntu-htl/readme erhält man genaustens beschrieben, wie die Installation, auszuführen in der Shell, funktioniert.

Im meinem Fall wird die gewünschte Seite, auf der sich die Anweisungen befinden, durch eine Störung sehr schlecht formatiert. Deswegen schreibe ich zur Hilfe die Befehle in das Protokoll:

**Erster Schritt:** Man muss sich als Super-User in der Shell anmelden, Passwort nicht vergessen!
```
liefrm17@Franz-Virtual-Box:~$ sudo -i
```

**Zweiter Schritt:** Die Befehle zur Installation des HTL Paketes:
```
root@Franz-Virtual-Box:~$ wget -O -http://www.htl-mechatronik.at/ubuntu-htl/install | bash
root@Franz-Virtual-Box:~$ apt update
root@Franz-Virtual-Box:~$ apt dist-upgrade
root@Franz-Virtual-Box:~$ apt install htl
```
------------------------------------------------------------------------------------------------------------------------
## Konfiguration des Lesezeichens in Firefox/Chrome
**In Arbeit...**

Hier finden Sie einen Link: https://support.mozilla.org/de/kb/Lesezeichen-sichern-und-wiederherstellen 

Auf dieser Website wird alles benötigte gut beschrieben.

--------------------------------------------------------------------------------------------------------------------
## Resümee
Die Ausführung dieses Arbeitsauftrages hat sich in gewissen Punkten schwieriger erwiesen als gedacht, obwohl alles von Haus aus ziemlich genau und bestens beschrieben war. Mit der Bedienung des eigenen Hausverstandes ist man in vielen Punkten sehr gut voran gekommen. Trotz der schwierigeren Kleinigkeiten ist alles bis zum Punkt "Installation des HTL-Paketes" reibungslos abgelaufen. Mit der Unterstützung und der Kompetenten Hilfe einiger Mitschüler, ist es eine leicht zu meisternde Aufgabe. Aber wie gesagt, in gewissen Punkten, die nicht beschrieben waren/sind, habe ich Unterstützung benötigt. 
