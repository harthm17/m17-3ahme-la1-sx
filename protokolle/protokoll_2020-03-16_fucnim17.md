# Installation von Ubuntu 18.04 LTS + Software in einer virtuellen Maschine
         
**Name**: Fuchshofer Niklas  
**Datum**: 16.03.2020  
**Klasse**: 3AHME  
**Gruppe**: 1  
------
------

## Inhaltsverzeichniss
1) [Download von VirtualBox](#download-von-virtualbox)
1) [Oracle VM VirtualBox Extension Pack installieren](#oracle-vm-virtualbox-extension-pack-installieren)
1) [Virtuelle Maschine erstellen](#virtuelle-maschine-erstellen)
     * [Hardwarevisualisierung aktivieren](#hardwarevisualisierung-aktivieren)
     * [Einstellungen treffen](#einstellungen-treffen)
1) [Ubuntu 18.04 installieren](#ubuntu-18.04-installieren)
1) [VirtualBox Guest Additions installieren](#virtualbox-guest-additions-installieren)
1) [Gemeinsamen Ordner erstellen]
1) [HTL-Paket installieren]
1) [Browser Lesezeichen-Menüleisete konfigurieren]


## Download von VirtualBox
Der erste Schritt war [VirtualBox](https://www.virtualbox.org/wiki/Downloads) zu installieren.
Dieser Schritt verlief relativ Problemlos.

## Oracle VM VirtualBox Extension Pack installieren
Anschließend mussten wir das [Oracle VM VirtualBox Extension Pack](https://download.virtualbox.org/virtualbox/6.1.4/Oracle_VM_VirtualBox_Extension_Pack-6.1.4.vbox-extpack) installieren.
In diesem SChritt mussten keine weiteren Mßnahmen getroffen werden, da die Installation komplett automatisch ablief.

## Virtuelle Maschine erstellen
### Hardwarevisualisierung aktivieren
Zuerst muss man im BIOS die Hardwarevisualisierung aktivieren. Dies ist von BIOS zu BIOS unterschiedlich.
### Einstellungen treffen
Zuerst einmal muss man unter dem Menüpunkt ```Neu``` ein neues virtuelles System erstellen. Man wird unter anderem nach dem Namen und den Ordner des Systems gefragt. Außerdem mussten wir bei ```Typ``` *Linux* und bei ```Version```*Ubuntu (64bit)* einstellen. 
Im nächsten Schritt muss man einige Einstellungen treffen, wie zum Beispiel die Anzahl der CPU-Kerne, wie viel Arbeitsspeicher mann freigeben will, auf welcher Festplatte man Ubuntu installieren will und man muss die [ISO-Datei für Ubuntu](https://ubuntu.com/download/desktop/thank-you?version=18.04.4&architecture=amd64) auswählen.
Einen weitereren wichtigen Punkt findet man unter ```Allgemein -> Erweitert```:
* Gemeinsame Zwischeneinlage: *bidirektional*
* Drag'n'Drop: *bidirektional*

## Ubuntu 18.04 installieren
Nun einfach die virtuelle Maschine starten und den Anweisungen der Installationssoftware folgen.
Dies erforderte keine speziellen Kompetenzen.

##  VirtualBox Guest Additions installieren
Bei neueren Versionen von Ubuntu ist dieses Paket schon installiert, doch wenn das nicht so sein sollte, folgendermaße vorgehen:
1) Virtuelle Maschine starten, in der die Guest Additions installiert werden sollen
1) Im Fenster der virtuellen Maschine auf den Menüpunkt ```Geräte```klicken
1) Auf ```Medium mit Gasterweiterungen einlegen```gehen
1) Auf ```VBoxWindowsAdditions.exe ausführen```klicken
