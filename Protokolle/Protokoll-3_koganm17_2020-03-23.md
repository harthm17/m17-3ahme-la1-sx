# Protokoll-3 LABOR/SX 3AHME (2019/20)

* **Thema:** Installation von Ubuntu 18.04 LTS + Software in einer virtuellen Maschine
* **Datum:** 23.03.2020
* **Gefehlt:** Keiner
* **Erstellt von:** koganm17
* **Protokoll letzte Einheit:** [02.12.2019](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/koganm17/Protokolle/Protokoll-2_koganm17_2019-12-02.md)

----------------------------------------------------------------------------------------------

## Inhaltsverzeichniss
1) [Download von VirtualBox](#download-von-virtualbox)
1) [Oracle VM VirtualBox Extension Pack installieren](#oracle-vm-virtualbox-extension-pack-installieren)
1) [Virtuelle Maschine erstellen](#virtuelle-maschine-erstellen)
     * [Hardwarevisualisierung aktivieren](#hardwarevisualisierung-aktivieren)
     * [Virtuelle Maschine](#virtuelle-maschine)
1) [Ubuntu 18.04 installieren](#ubuntu-18.04-installieren)
1) [VirtualBox Guest Additions installieren](#virtualbox-guest-additions-installieren)
1) [Gemeinsamen Ordner erstellen](#gemeinsamen-ordner-erstellen)
1) [HTL-Paket installieren](#htl-paket-installieren)
1) [Browser Lesezeichen-Menüleisete konfigurieren](#browser-lesezeichen-menüleisete-konfigurieren)

----------------------------------------------------------------------------------------------

## Download von VirtualBox

Zuerst ladet man [VirtualBox](https://www.virtualbox.org/wiki/Downloads) herunter. Dann muss man den Installationspfad angeben und ein paar mal weiterdrücken. Das ging bei mir problemlos vonstatten. 

----------------------------------------------------------------------------------------------

## Oracle VM VirtualBox Extension Pack installieren
Anschließend muss man [Oracle VM VirtualBox Extension Pack](https://download.virtualbox.org/virtualbox/6.1.4/Oracle_VM_VirtualBox_Extension_Pack-6.1.4.vbox-extpack) installieren.
Das ist ein Zusatzpaket. Auch dieser Schritt war kein Problem.

----------------------------------------------------------------------------------------------

## Virtuelle Maschine erstellen
### Hardwarevisualisierung aktivieren
Zuerst muss man im BIOS die Hardwarevisualisierung aktivieren. Ins BIOS kommt man beim Starten des PCs indem man die richtige Taste spamt.  Die Visualisierung aktiviert man im Bios unter ```erweiterten Einstellungen``` und hier sucht man die ```SVM``` und aktiviert diese.
### Virtuelle Maschine
Zuerst muss man unter dem Menüpunkt ```Neu``` ein neues virtuelles System erstellen. Man muss nun den Namen,den Ordner, den Typ und die Version des Systems eingeben. 
Im nächsten Schritt muss man einige Einstellungen treffen wie den Arbeitsspeicher und den Festplattenspeicher. Ich habe 4 GiB RAM und 50GiB Festplattenspeicher ausgewählt.
Jetzt muss man noch folgendes einstellen. unter ```Allgemein -> Erweitert```:

----------------------------------------------------------------------------------------------

## Ubuntu 18.04 installieren
Jetzt muss man die [ISO-Datei für Ubuntu](https://ubuntu.com/download/desktop/thank-you?version=18.04.4&architecture=amd64) herunterladen und in der virtuellen Maschine installieren.
Nun einfach die virtuelle Maschine starten und den Anweisungen der Installationssoftware folgen.

----------------------------------------------------------------------------------------------

##  VirtualBox Guest Additions installieren
Bei neueren Versionen von Ubuntu ist dieses Paket schon installiert, doch wenn das nicht so sein sollte, folgendermaße vorgehen:
1) Virtuelle Maschine starten, in der die Guest Additions installiert werden sollen
1) Im Fenster der virtuellen Maschine auf den Menüpunkt ```Geräte```klicken
1) Auf ```Medium mit Gasterweiterungen einlegen```gehen
1) Auf ```VBoxWindowsAdditions.exe ausführen```klicken

----------------------------------------------------------------------------------------------

## Gemeinsamen Ordner erstellen
Jetzt erstellen wir einen gemeinsamen Ordner auf den man von beiden Betriebssystemen aus zugreifen kann. 
1) Ordner am Host-System erstellen (z.B. am Desktop)
1) Im VirtualBox Hauptmenü auf ```Geräte```gehen
1) Bei ```Gemeinsame Ordner```auf das grüne Plus klicken
1) Den gewüschten Ordner auswählen

Nun kann man noch folgende Einstellungen treffen:
* Gemeinsame Zwischeneinlage: *bidirektional*
* Drag'n'Drop: *bidirektional*

----------------------------------------------------------------------------------------------

## HTL-Paket installieren
Beim Installieren des HTL-Paketes geht man nach [dieser](http://www.htl-mechatronik.at/ubuntu-htl/readme) Beschreibung vor.

----------------------------------------------------------------------------------------------

## Browser Lesezeichen-Menüleisete konfigurieren
[Hier](https://support.mozilla.org/de/kb/Lesezeichen-sichern-und-wiederherstellen) ist dieser Arbeitsschritt gut erklärt.
