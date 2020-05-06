# Protokoll LA1/SX 3AHME (2019/20)

* **Thema:** Installation einer virtuellen Maschine mit Ubuntu 20.04
* **Datum:** 04.05.2020
* **Gefehlt:** -
* **Erstellt von:** Peyer Kassandra

----------------------------------------------------------------------------------------------
## Inhaltsverzeichnis

1. [Donload und Installation von VirtualBox](#donloadundinstallationvonvirtualbox)
2. [VirtualBox Extension Pack installieren](#virtualboxextensionpackinstallieren)
3. [Die virtuelle Maschine erstellen und Ubuntu installieren](#dievirtuellemaschineerstellenundubuntuinstallieren)
4. [Installation von den VirtualBox Guest Additions](#installationvondenvirtualboxguestadditions)
5. [Einen Gemeinsamen Ordner erstellen](#einengemeinsamenordnererstellen)
6. [HTL-Paket installieren](#htl-paketinstallieren)
7. [Lesezeichen in Firefox und Chromium importieren](#lesezeicheninfirefoxundchromiumimportieren)

----------------------------------------------------------------------------------------------
## Donload und Installation von VirtualBox

Als Erstes muss man die VirtualBox für sein Betriebssystem [hier](https://www.virtualbox.org/wiki/Downloads) herunterladen und 
gleich danach ausführen, um die VirtualBox auf seinem Rechner zu installieren.

## VirtualBox Extension Pack installieren

Als nächstes ist es Ratsam dieses [Extension Pack](https://download.virtualbox.org/virtualbox/6.1.6/Oracle_VM_VirtualBox_Extension_Pack-6.1.6.vbox-extpack) 
herunterzuladen. Um es zu installieren muss man es einfach ausführen und den Anweisungen auf dem Bildschirm folgen.

## Die virtuelle Maschine erstellen und Ubuntu installieren

Um eine virtuelle Maschine anzulegen muss man bei der VirtualBox unter **Maschine** -> **Neu** eine erstellen. Man muss ihr einen Namen geben, 
ihr Betriebssystem auswählen und dessen Version. Danach muss man die RAM, welche man der Maschine zu Verfügung stellt auswählen. Hier ist 
es Ratsam 4GB oder mehr auszuwählen da bei zu wenig RAM (z.B. 1GB) die Maschine(bei heutigen Betriebssystemen) nicht stabil laufen kann. 
Der nächste Schritt beinhaltet das Hinzufügen einer Festplatte. Bei unserem Vorhaben sollte man eine Festplatte mit der festen Größe von 
100GB erzeugen.

Als nächstes muss man die neueste Version von [Ubuntu]() als Datenträgerimagedatei(ISO Datei) herunterladen. Um diese Datei bei der 
virtuellen Maschine "einzulegen" muss man unter **Ändern**, wie hier gezeigt bei **Abbild auswählen** die gewünschte ISO-Datei auswählen.

![](https://cdn.discordapp.com/attachments/616366786975236099/707666453695823973/VM_Anleitung.png)

Danach muss man die virtuelle Maschine starten und das Installationsprogramm von Ubuntu wird ausgeführt.

## Installation von den VirtualBox Guest Additions

Um die Guest Additions richtig zu installieren muss man diese Befehle in die shell eingeben.

```
sudo add-apt-repository multiverse
sudo apt install virtualbox-guest-dkms virtualbox-guest-x11
```

Nach dem die Packages fertig heruntergeladen wurden muss man die virtuelle Maschine neu starten.

## Einen Gemeinsamen Ordner erstellen

Um zwischen dem Wirtsystem und Gastsystem einen gemeinsamen Ordner zu erstellen muss man bei **Ändern** unter **Gemeinsame Ordner** auf das 
grüne Plus drücken.

![](https://cdn.discordapp.com/attachments/616366786975236099/707674123874074655/VM_Anleitung2.png)

In unserem Fall soll der Ordner unter /work beim Gastsystem eingebunden werden.

## HTL-Paket installieren

Um dieses Paket zu installieren muss man die in dieser [Anleitung](http://www.htl-mechatronik.at/ubuntu-htl/readme) stehende Befehle ausführen.

## Lesezeichen in Firefox und Chromium importieren

Bei Firefox muss man einfach unter **Lesezeichen** auf **Lesezeichen verwalten** drücken. Dann muss man auf **Wiederherstellen** -> **Datei auswählen** 
und die richtige JSON Datei auswählen. 

Bei Chromium muss man unter **Lesezeichen** -> **Lesezeichen-Manager** klicken, dann auf die drei Punkte und danch auf **Lesezeichen importieren** klicken.











