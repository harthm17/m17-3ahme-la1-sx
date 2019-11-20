# 1. Protokoll

-------------------------------------------------

## Thema: Versionsverwaltung bzw. Markdown

-------------------------------------------------

Übungsdatum:   Montag, 18.11.2019     
Übungszeit:    14:10 bis 16:20      
Übungsort:     Arnfels, CAD-Saal    
Verfasser:     Georg Kaufmann    
Abwesend:      keiner      
Anwesend:      Felix Hamrle, Stefan Haring, Thomas Harrer, Georg Kaufmann, Andreas Kogler, Franz Lieleg, Simon Marcher

-------------------------------------------------

### Inhaltsverzeichnis
1) [Versionsverwaltungssysteme](#versionsverwaltungssysteme) 
    * [Grundlagen](#grundlagen) 
    * [Vorteile](#vorteile) 
    * [Verschiedene Systeme](#verschiedene-systeme)
1) [Dokumentation](#dokumentation) 
1) [Markdown](#markdown)
    * [Formatierung](#formatierung)
    * [Grundlagen](#grundlagen)
1) [Github](#github)
    * [Ebenen und Branches](#ebenen-und-branches)
      * [Ebenen](#ebenen)
      * [Branches](#branches)
      * [Befehle](#befehle)
  
-------------------------------------------------

### Themen des ersten Laborzyklus:
1. Versionsverwaltung, Markdown (Protokoll) - 18.11.2019
1. LINUX Grundlagen Teil 1 - 25.11.2019
1. LINUX Grundlagen Teil 2 (Test + Protokoll) - 02.12.2019

-------------------------------------------------

### Versionsverwaltungssysteme
#### Grundlagen
Immer wenn es eine neue **Version** entsteht wird diese in einer Datenbank hochgeladen.   
Es ist z.B. feststellbar wer die neue Version hochgeladen hat, wann diese hochgeladen wurde, was hochgeladen wurde und vieles mehr. 

Laut Wikipedia:
> Eine Versionsverwaltung ist ein System, das zur Erfassung von Änderungen an Dokumenten oder Dateien verwendet wird.

Ein gutes Beispiel für solch eine Versionsverwaltung ist [Wikipedia](https://www.wikipedia.org/). 
Zu aller erst wird ein Eintrag über ein bestimmtes Thema erstellt, anschließend kann man diesen verändern und es werden verschiedene Versionen gespeichert.

#### Vorteile
* Wenn ein Fehler entsteht kann man einfach zu einer Funktionierenden Version zurückspringen.
* Team working, eine Versionsverwaltung ist perfekt dafür geeignet. 
* Ich habe von überall Zugriff über einen anderen PC.
* **Wichtig** ist der Schutz vor sich selbst. Wenn ich eine Datei zerstöre kann ich einfach zu einer vorigen springen.

#### Verschiedene Systeme
Ein gutes Beispiel für solch eine Versionsverwaltung ist **GIT**. Zurück zu führen ist diese auf Linus Torvalds, ebenfalls wichtige Entwicklungen von ihm waren beispielsweiße Linux.

Der Name ist folgendermaßen Zustande gekommen:
Git ist im britischen der Ausdruck für "Blödmann" und Linus Torvald begründete seine Namens Entscheidung mit folgendem Satz.
>“I’m an egotistical bastard, and I name all my projects after myself. First ‘Linux’, now ‘Git’.”

Die Web-Plattform für solche GIT verwaltete Projekte ist Github. Vor gut einem Jahr kaufte sich Microsoft für umgerechnet 6,4 Milliarden Euro Github. Seither hat sich schon einiges geändert, zwecks einfacher Handhabung. 
Die Web-Plattform ist eine Open Source Plattform und jeder kann die Dinge anderer einsehen und lesen.  

![Bild](https://de.wikipedia.org/wiki/Git#/media/Datei:SVNvsGITServer_2.png)

-------------------------------------------------

### Dokumentation
Arten der Dokumenatiotn | Pro                                                          | Kontra
----------------------- | ---                                                          | ------
handschriftlich         | flexibel, schnell                                            | unleserlich, elektronischen Suchen, unübersichtlich
Schreibmaschine         |                                                              |
Textverarbeitung        | leserlich, übersichtlich, elektronisches Suchen, veränderbar | Zeitbedarf

-------------------------------------------------

### Markdown
#### Formatierung
***Anwendungsname***       | ***Umsetzung/Anwendung***
--------------             | -------------------
**Überschrift**            | #
**Unterüberschrift**       | ## bis zu sechs Unterüberschriften/Hashtags
**Zeilenumbruch**          | 2 * Tabulator
**Text fett**              | **Beispiel** - \*\*Beispiel** 
**Text kursiv**            | *Beispiel* - \*Beispiel*
**Text kursiv + fett**     | ***Beispiel*** - \*\*\*Beispiel***
**Link**                   | Siehe \[Beispiel](https:// ... )
**Bild**                   | Siehe \![Beispiel](https:// ... )
**Video**                  | gleich wie bei "Bild"
**Quelltext**              | drei ´´´ Hochstriche am Anfang und drei ´´´ Hochstriche am Ende
**Zitat**                  | > Beispiel Satz nicht vorhanden
**Verlinkung der Überschrift** | \[Beispiel Beispiel](#beispiel-beispiel)
**Aufzählung**             | * Beispiel 1 (durch einen Stern vor dem Satz) oder 1. Beispiel (durch eine Eins Punkt vor dem Satz, er bessert automatisch aus auf 2. 3. usw.)
**Tabelle**                | siehe [Tabelle](https://thoughtbot.com/blog/align-github-flavored-markdown-tables-in-vim)

#### Grundlagen
Markdown ist eine Auszeichnungssprache. Das Ziel ist es, Texte mit wenig Aufwand übersichtlich darstellen zu können. Die Formatierung geschieht durch einfache Befehle (siehe oben).
Meistens werden für die Auszeichnung Satzzeichen verwendet.  

-------------------------------------------------

### Github
#### Ebenen und Branches
##### Ebenen
Es gibt verschiedene Ebenen um auch offline arbeiten zu können.
![Bild](https://camo.githubusercontent.com/5a4967992d07a6f0f97422e6de4296edcbbe6050/68747470733a2f2f72656164736168696c2e66696c65732e776f726470726573732e636f6d2f323031362f30392f6769745f63686561745f73686565742e706e673f773d36333667)

Die Befehle die man dafür benötigt sind unten angeführt.

##### Branches
Um sich nicht in die quere zu kommen gibt es sogenannte Branches. Diese dienen dazu das man ungestört arbeiten kann.

![Bild](https://camo.githubusercontent.com/fe7346b2099985eecb0aa828d84a84432187fbec/68747470733a2f2f6172636377696b692e7577796f2e6564752f696d616765732f312f31392f4769744875625f466c6f775f73746570732e706e67)

##### Befehle
git clone https://...      
git checkout maxmuster     
gedit README.md      
git add README.md    
git commit -m"UpdateREADME"      
git push    
