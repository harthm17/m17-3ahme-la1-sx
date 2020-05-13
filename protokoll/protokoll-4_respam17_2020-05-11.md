# Protokoll 4 Labor-SX 2020
--------------------------------
## Virtuelle Maschine/Arbeitsauftrag 1 fertigstellen
* **Datum:** 11.05.2020
* **Fehlend:** --
* **Erstellt von:** Resch Paul
* **Übungsort:** Wegen Corona im Home-Office
----------------------
### Inhaltsangabe
* [Diskussion](#diskussion)
* [HTL-Paket](#htl-paket)
* [Chromium](#chromium-browser)
    * [Installation](#installation)
* [Lesezeichen](#lesezeichen-und-menüleiste)
    * [Konfiguration](#konfiguration)
    * [Firefox](#firefox)
    * [Chromium](#chromium)

---------------
### Diskussion
Diskussion mit einem Kollegen der mit Punkt 6 der Aufgabenstellung noch Schwierigkeiten hatte (Verzeichnis zwischen Gastsystem und Host System) und ich das selbe Problem in der letzten Unterrichteinheit gelöst habe.

---------------------------------
### HTL-Paket
[Installieren des HTL-Paketes](http://www.htl-mechatronik.at/ubuntu-htl/readme) mit Hilfe von Kommandso in der Konsole.
Zunächst werden alle Dateien heruntergeladen und in den nächsten Schritten endpackt und installiert.
Empfohlen ist es die Angabe zur Installation des Paketes auf einem Linux-System zu lesen.

---------------------------------
### Chromium-Browser

#### Allgemeines
Chromium hört sich nicht ohne Grund ähnlich wie Chrome an. Unter diesem Namen wird Google Chrome praktisch als [Open-Source-Projekt](https://de.wikipedia.org/wiki/Open_Source) zur Verfügung gestellt.

Weitere Informationen zum Browser [hier](https://de.wikipedia.org/wiki/Chromium_(Browser)) (Wikipedia).

#### Installation
Zum Download muss man nicht viel sagen, da alles automatisch funktionieren sollte. Man kann es einfach im Internet oder mit Hilfe eines Kommandos sehr einfach downloaden. Genaueres [hier](https://wiki.ubuntuusers.de/Chromium/Installation/).
> sudo apt-get install chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg

----------------------------------
### Lesezeichen und Menüleiste
Mit sogenannten Lesezeichen kann man in einem Browser sehr einfach Websites speichern. Die erforderlichen Lesezeichen an der Menüleiste sind als *html-Datei* im [HTL-Paket](#htl-paket) enthalten. Im Browser werden diese dann an der Menüleiste angezeigt und sehen aus wie Ordner. Diese sollen in den beiden Browsern (Firefox und Chromium) vorhanden sein.

#### Konfiguration
Um die Lesezeichen wie erforderlich darzustellen, muss man einige Schritte beachten. Das Anleitungsvideo in unserer Angabe beschreibt diese (Link für das Video nicht im Protokoll).

Hier zusammengefasst:

##### Firefox

* Auf das *Bücheregal* klicken (rechts oben neben der Suchleiste)
* Kategorie *Lesezeichen* wählen
* Ganz unten auf *Lesezeichen verwalten* klicken
* Ein neuse Fenster sollte sich öffnen
* Register *Importieren und Sichern* und den Unterpunkt *Wiederherstellen* klicken
* Anshließend auf *Datei wählen...* klicken
* Jetzt nur noch die gewünschte html-Datei wählen und die Lesezeichen sollten angezeigt werden
    * Pfad für unsere erforderlichen Lesezeichen: **/usr/share/htl/links/firefox**
    
##### Chromium

Hier gab es ein paar Schwierigkeiten, welche aber gelöst wurden. Im Video wurde erklärt wie man mit Hilfe von Kommandos die Lesezeichen einrichtet. Da für die Installation von Chromium ein anderer Pfad verwendet wurde war es mit nicht möglich, die Lesezeichen trotz probieren in der Konsole einzurichten.

Schritte um trotzdem ans Ziel zu kommen:
* In Chromium auf das *3-Punkte-Menü* klicken
* Kategorie *Lesezeichen* und Unterpunkt *Lesezeichen-Manager* wählen
* Auf das blau hinterlegte *3-Punkte-Menü* klicken
* *Lesezeichen importieren* wählen und Gewünschte Datei auswählen

Da diese Methode bei mir ebenfalls nicht funktionierte, habe ich recherchiert und eine andere Methode gefunden.
* *Firefox* öffnen
* Auf das *Bücherregal* klicken
* *Lesezeichen* wählen
* *Lesezeichen verwalten*
* *Importieren und Sichern*
* Den Punkt *Lesezeichen nach HTLM exportieren...* wählen
* Gewünschte Datei wählen und am besten am Schreibtisch speichern
* Oben angeführte Punkte widerholen











