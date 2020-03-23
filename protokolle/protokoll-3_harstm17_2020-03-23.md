# Protokoll-3 LABOR/SX 3AHME (2019/20)

---------------------------------------------------------------------------------------------

* **Thema:** Installation von Ubuntu 18.04 LTS + Software in einer virtuellen Maschine
* **Datum:** 23.03.2020
* **Gefehlt:** -
* **Erstellt von:** Stefan Haring (harstm17)
* **Protokoll der letzten Einheit:** [Protokoll 2](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/harstm17/protokolle/protokoll-2_harstm17_2019-12-02.md)

----------------------------------------------------------------------------------------------

## Inhaltsverzeichnis  

1. [Download von Virtualbox](#download-von-virtualbox)
1. [Oracle VM VirtualBox Extension Pack installieren](#oracle-vm-virtualbox-extension-pack-installieren)
1. [Virtuelle Maschine erstellen](#virtuelle-maschine-erstellen)
    * [Abbild erstellen](#abbild-erstellen)
    * [Visualisierung](#visualisierung)
1. [Guest Additions installieren](#guest-additions-installieren)
1. [Verzeichnis zwischen Gastsystem und virtuellen System erstellen](#verzeichnis-zwischen-gastsystem-und-virtuellen-system-erstellen)
1. [HTL Paket installieren](#htl-paket-installieren)
1. [Menüleiste konfigurieren](#menüleiste-konfigurieren)

-------------------------------------------------------------------------------------

### Download von Virtualbox

Unter folgendem Link kann man Virtualbox auf seinem jeweiligen Betriebssystem herunterladen und anschließend installieren. Dieser Schritt sollte problemlos verlaufen, solang genügend Speicherplatz und eine funktionierende Internetverbindung gewährleistet ist.

[Virtualbox Download](https://www.virtualbox.org/wiki/Downloads)

----------------------------------------------------------------------------------------

### Oracle VM VirtualBox Extension Pack installieren

Hierbei gilt es wieder, dem [Link](https://download.virtualbox.org/virtualbox/6.1.4/Oracle_VM_VirtualBox_Extension_Pack-6.1.4.vbox-extpack) zu folgen. Der Download des Exstension Packs startet danach automatisch und man kann dann sofort mit der Installation beginnen. Dieses Pack ist nicht dringend notwendig um die Virtualbox nutzen zu können.

-----------------------------------------------------------------------------------------

### Virtuelle Maschine erstellen

#### Hardwarevisualisierung aktivieren
Zuerst muss man im BIOS die Hardwarevisualisierung aktivieren. Dies ist von BIOS zu BIOS unterschiedlich. Die Visualisierung habe ich in meinem BIOS unter```Erweiterte Einstellungen``` und anschließendem Suchen nach ```SVM``` aktiviert. Um überhaupt ins BIOS zu kommen, verhelfen einem verschiedene Tastenkombinationen, die beim Start des PC getätitgt werden müssen. Bei meinem PC kam ich trotz langem Probieren von verschiedensten Kombinationen, die mir im Internet offenbart worden sind nicht ins BIOS und musste dann mit Hilfe der Windows-Settings dort hin gelangen.

#### Einstellungen vornehmen
1) Unter dem Punkt ```Neu``` gibt man einen beliebigen Namen für das virtuelle System ein und wählt den gwünschten Speicherort für das System aus. Hierbei kann es sein, dass eine Fehlermeldunng aufkommt, wenn die zuvor installierten Dateien auf verschiedenen Festplatten gespeichert sind. Beim folgenden Schritt muss man den Typ auswählen und der sollte in unserem Fall Linux lauten. Anschließend wählt man unter Version Ubuntu (64bit) aus.

1) Damit das System einwandfrei läuft sollte man mindestens 4GB RAM zur verfügung stellen. Zu beachten ist hierbei jedoch, einen PC zu haben der mehr als 4GB RAM hat, da man den gesamten Arbeitsspeicher nicht für die virtuelle Maschine verwenden soll.

1) Nächsteres muss man den Festplattenspeicher auswählen. Die Empfehlung lag bei mindestens 50GiB, doch meiner Meinung nach bin ich mit meinen ausgewählten 40GiB schon auf der sicheren Seite.

1) Danach ```Festplatte erzeugen``` und ```VDI (VirtualBox Disk Image)``` wählen. Bei der Art der Speicherung sollte man ```dynamisch alloziert``` wählen da es bei ```feste Größe``` oft zu Systemabstürzen kommt.

Jetzt ist das Virtuelle System erstellt und man sollte noch ein paar Feineinstellungen vornehmen, welche man unter den folgenden Punkten ändern kann:
```
* allgemein
      * erweitert
         Gemeinsame Zwischenablage: "bidirektional"
                       Drag'n'Drop: "bidirektional"
```

#### Massenspeicher verwalten
```
* Massenspeicher
      * Controller: IDE
      |- leer 
      
      Hier leer auswählen und rechts bei "Optisches Laufwerk": neben "Sekundärer Master"
      befindet sich eine kleine blaue CD, diese beklickt man doppelt 
      und unter "Datei für Optisches Medium auswählen" wählt man    
      dann die vorher heruntergeladene Ubuntu.iso Datei aus.
```

[Ubuntu Datei:](https://ubuntu.com/download/desktop/thank-you?version=18.04.4&architecture=amd64)

#### Virtuelle Maschine starten
Nach der Abfolge dieser Schritte, sollte einem Start der virtuellen Maschine nichts mehr im Wege stehen.

----------------------------------------------------------------------------------------------------

### Guest Additions installieren
Bei neueren Ubuntu-Versionen sind die Guest Additions bereits vorinstalliert, falls dies nicht der Fall sein sollte, kann man sie wie folgt manuell installieren.

* Virtuelle Maschine starten, in der die Guest Additions installiert werden sollen.
* Im Fenster der virtuellen Maschine auf den Menüpunkt ```Geräte```klicken.
* Auf ```Medium mit Gasterweiterungen einlegen``` klicken.
* Anschließend ```VBoxWindowsAdditions.exe ausführen``` ausführen.

---------------------------------------------------------------------------------------------------

### Verzeichnis zwischen dem Gastsystem und dem Wirtsystem erstellen
Eignet sich sehr gut zum Datentransfer zwischen den beiden Systemen.

Zuerst erstellt man einen Ordner auf dem Host-System.
Danach geht man wie folgt vor:
```
   *Ändern
      *Gemeinsame Ordner
      - unter diesem Punkt kann man beim "grünen Plus" den Ordner hinzufügen.
```
-----------------------------------------------------------------------------------------------------

### HTL Paket installieren
Beim Installieren des HTL-Paketes geht man Laut [dieser](http://www.htl-mechatronik.at/ubuntu-htl/readme) Beschreibung vor.

---------------------------------------------------------------------------------------------------

### Lesezeichen Menüleiste in Firefox und Chromius konfigurieren
Ziel ist es, alle verfügbaren Ressourcen der Lesezeichen Menüleiste, die es in der Schule gibt zu nutzen.

#### Konfigurieren der Lesezeichen in Firefox
zu befolgende Schritte:
1. Firefox öffnen
1. Rechts von der Suchleiste auf das erste Symbol klicken.
1. Anschließend "Lesezeichen" und dann "Lesezeichen verwalten auswählen
1. Danach in der obersten Leiste auf "Importieren und Sichern" 
1. Dort auf "Lesezeichen von HTML importieren" klicken und anschließend die bestehende HTML-Datei auswählen.
1. Die Lesezeichenleiste einschalten, falls dies noch nicht erledigt wurde.

#### Konfigurieren der Lesezeichen in Chromius
zu befolgende Schritte:
1. Chromius öffnen und in die Suchleiste ```chrome://bookmarks``` eingeben.
1. In der blauen Leiste auf die drei Punkte klicken und auf ```Lesezeichen importieren``` klicken.
1. Jetzt muss nur mehr die zu wünschende HTML-Datei ausgewählt werden, diese dann mit ```OK``` bestätigt werden und schon ist man fertig.
