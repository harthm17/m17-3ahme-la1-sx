# Protokoll Virtual Box installieren

-----

**Name**: Andreas Augustin  
**Datum**: 16.03.2020  
**Klasse**: 3AHME  
**Gruppe**: 1  

-----

## Inhaltsverzeichniss  

1) [Download von Virtualbox](#download-von-virtualbox)
1) [Virtualbox Extension Pack installieren](#virtualbox-extension-pack-installieren)
1) [Virtuelle Maschine erstellen](#virtuelle-maschine-erstellen)
    * [Abbild erstellen](#abbild-erstellen)
    * [Visualisierung](#visualisierung)
1) [Guest Additions installieren](#guest-additions-installieren)
1) [Verzeichnis zwischen Gastsystem und virtuellen System erstellen](#verzeichnis-zwischen-gastsystem-und-virtuellen-system-erstellen)
1) [HTL Paket installieren](#htl-paket-installieren)
1) [Menüleiste konfigurieren](#menüleiste-konfigurieren)

-----

# Download von Virtualbox

Einfach das jeweilige Paket für das Host-Betriebssystem auswählen und installieren.

[Virtualbox](https://www.virtualbox.org/wiki/Downloads)

-----

# Virtualbox Extension Pack installieren

Mit dem folgenden Link wird das Paket automatisch gedownloadet. Danach einfach die Datei ausführen und fertig installieren.

[Extension Pack:](https://download.virtualbox.org/virtualbox/6.1.4/Oracle_VM_VirtualBox_Extension_Pack-6.1.4.vbox-extpack)

-----

# Virtuelle Maschine erstellen

Unter dem Punkt ```Neu``` gibt man einen beliebigen Namen für das virtuelle System ein und gibt einen Ordner für das System an. Bei Typ sollte man Linux wählen und unter Version wählt man Ubuntu (64bit).

Damit das System "flüssig" läuft sollte man minimum 4 GB ram dem virtuellen system zuweisen.

Danach ```Festplatte erzeugen``` und ```VDI (VirtualBox Disk Image)``` wählen. Bei der Art der Speicherung sollte man ```dynamisch alloziert``` wählen da es bei ```feste Größe``` (wenn man die Größe übersieht) zu System abstürzen führen kann.

Jetzt ist das Virtuelle System erstellt und man sollte noch ein paar einstellungen vornehmen unter dem Punkt ändern:
```
* allgemein
      * erweitert
         Gemeinsame Zwischenablage: "bidirektional"
                       Drag'n'Drop: "bidirektional"
```
### Abbild erstellen
```
* Massenspeicher
      * Controller: IDE
      |- leer 
      
      Hier leer auswählen und rechts bei Optisches Laufwerk: Sekundärer Master
      Danaben befindet sich eine kleine blaue Cd, diese wählt man aus 
      und unter "Datei für Optisches Medium auswählen" wählt man    
      dann die vorher heruntergeladene Ubuntu.iso Datei.
```

[Ubuntu Datei:](https://ubuntu.com/download/desktop/thank-you?version=18.04.4&architecture=amd64)

### Visualisierung

Es kann sein das bei gewissen Systemen die Visualisierung deaktiviert ist und somit lässt sich das Virtuelle System nicht starten.  
Die Visualisierung aktiviert man im Bios unter "erweiterten Einstellungen" und hier sucht man die "SVM" und aktiviert diese. Das ist natürlich von Bios zu Bios unterschiedlich.

Nach diesen Schritten kann man das virtuelle System starten.

Nun folgt man einfach den ganzen Installationsverlauf und installiert Ubuntu fertig auf dem virtuellen System.

-----

# Guest Additions installieren

Bei den neueren Ubuntu versionen sind die Guest Additions bereits vorinstalliert jedoch kann man sie auch manuel installieren.

Sobald man im Virtuellen System ist kann beim Oracle Fenster unter ```Geräte``` ```Gasterweiterungen einlegen``` das Paket installieren.

# Verzeichnis zwischen Gastsystem und virtuellen System erstellen

Zuerst erstellt man einen Ordner auf dem Host-System.

Danach geht man wie folgt vor:
```
   *Ändern
      *Gemeinsame Ordner
      - unter diesem Punkt kann man beim "grünen Plus" den Ordner hinzufügen.
```

# HTL Paket installieren

Beim installieren dieses Paket's geht man wie beschrieben auf dieser Seite vor:

[HTL Paket](http://www.htl-mechatronik.at/ubuntu-htl/readme)

# Menüleiste konfigurieren

Diesen Punkt habe ich nicht geschafft zu erledigen. Habe mich mit Niklas Fuchshofer unterhalten, der es auch nicht hat, und dann hat er mir diesen Link zukommen lassen, der diese Aufgabe sehr gut beschreibt.

[konfiguration](https://support.mozilla.org/de/kb/Lesezeichen-sichern-und-wiederherstellen)
