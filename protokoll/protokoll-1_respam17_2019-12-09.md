# Protokoll 1 Labor-SX 2019/20
---------------------------------
* **Thema:** Versionsverwaltung
* **Datum:** 09.12.2019
* **Fehlend:** --
* **Erstellt von:** Paul Resch
---------------------------------
## Inhaltsverzeichnis
1. [Themen der Einheiten](#themen-der-einheiten)
1. [Versionsverwaltung](#versionsverwaltung)
    * [Definition](#definition)
    * [Vorteile](#vorteile)
    * [Nachteile](#nachteile)
1. [Dokumentieren](#dokumentieren)
    * [Handschriftlich](#handschriftlich)
    * [Bild](#bild-erstellen)
    * [Textverarbeitung](#textverarbeitung)
1. [Markdown](#markdown)
1. [Branch](#branch)
---------------------------------
### Themen der Einheiten
1. Einheit: Versionsverwaltung, Dokumentation mit Markdown bzw. Web (Protokoll)
1. Einheit: Linux Grundlagen 1 (Test)
1. Einheit: Linux Grundlagen 2 (Protokoll)
----------------------------------
### Versionsverwaltung
manchmal auch *Code Version System (CVS)* 
* #### Definition
Definition laut [Wikipedia](https://de.wikipedia.org/wiki/Versionsverwaltung):
 > Eine Versionsverwaltung ist ein System, das zur Erfassung von Änderungen an Dokumenten oder Dateien verwendet wird. Alle Versionen werden in einem Archiv mit Zeitstempel und Benutzerkennung gesichert und können später wiederhergestellt werden. Versionsverwaltungssysteme werden typischerweise in der Softwareentwicklung eingesetzt, um Quelltexte zu verwalten.

Alle Versionen von zB. einem Projekt werden in einer Datenbank ***(Repository)*** gespeichert.

[Repository (Wikipedia)](https://de.wikipedia.org/wiki/Repository)

* #### Vorteile
1) Zugriff auf alle bisherigen Varianten/Versionen *-> es geht nichts verloren*
1) Alles bleibt gespeichert *-> zB. Fehler nachweislich*
1) Grundlage für Teamworking
1) Übersichtlich
1) "Schutz vor sich selbst" (man macht Laptop/PC kaputt; etc.)

* #### Nachteile
1) Umgang muss erlernt werden
1) bei kostenloser Version kann jeder auf Daten zugreifen
----------------------------------

### Dokumentieren

#### Dokumentieren Allgemein
Definition laut [Wikipedia](https://de.wikipedia.org/wiki/Dokumentation):
> Unter Dokumentation versteht man die Nutzbarmachung von Informationen zur weiteren Verwendung.
1) #### Handschriftlich
* **Vorteile:** 
  * schnell 
  * oft verfügbar
* **Nachteile:** 
  * manchmal unleserlich 
  * verbreitung schwierig
  * kein Backup 
  * nicht elektronisch verarbeitbar
(man kann zB. nicht nach bestimmten Wörtern suchen) 

2) #### Bild erstellen

    mit zB. einem Smartphone
* **Vorteile:** 
  * schnell
  * oft verfügbar
  * gut verbreitbar
  * Backup
* **Nachteile:** 
  * elektronisch nicht verarbeitbar
  * Speicherplatz
  
3) #### Textverarbeitung
* **Vorteile:**
  * elektronisch verarbeitbar
  * gut verbreitbar
  * Backup
  * immer leserlich
* **Nachteile:**
  * Zeitaufwendig
    
4) #### Markdown (Web)

Soll alle Vorteile kombinieren

-----------------------------------

### Markdown

[Markdown](https://de.wikipedia.org/wiki/Markdown) aus Wikipedia:
> Markdown ist eine vereinfachte Auszeichnungssprache, die von John Gruber und Aaron Swartz entworfen und im Dezember 2004 mit Version 1.0.1 spezifiziert wurde. Ein Ziel von Markdown ist, dass schon die Ausgangsform ohne weitere Konvertierung leicht lesbar ist.

Markdown kombiniert Vorteile vom Dokumentieren mit Textverarbeitung, soll aber auch schnell funktionieren wie zB. das Handschriftliche dokumentieren.

Dateiendung ist entweder *.md* oder *.markdown*.

-----------------------------------

### Branch

[Branch(Abspaltung/Zweig)](https://de.wikipedia.org/wiki/Abspaltung_(Softwareentwicklung)) laut Wikipedia:
> Eine Abspaltung (auch Fork; englisch fork ‚Gabel‘, üblicherweise im Maskulinum verwendet) ist in der Softwareentwicklung ein Entwicklungszweig nach der Aufspaltung eines Projektes in zwei oder mehrere Folgeprojekte; die Quelltexte oder Teile davon werden hierbei unabhängig vom ursprünglichen Mutterprojekt weiterentwickelt.

In GitHub gibt es einen *Masterbranch*. Jedoch arbeitet man nicht in diesem sondern erstellt einen Nebenzweig (Nebenbranch).
Anschließend kann man den Nebenbranch wieder zurück zum Masterbranch bringen. 

----------------------------------

### GitHub

> [Github](https://de.wikipedia.org/wiki/GitHub) ist ein Onlinedienst, der Software-Entwicklungsprojekte auf seinen Servern bereitstellt (Filehosting). Namensgebend war das Versionsverwaltungssystem Git. Die GitHub, Inc. hat ihren Sitz in San Francisco in den USA. Ähnliche Dienste sind GitLab und Bitbucket. Seit 26. Dezember 2018 gehört das Unternehmen zu Microsoft.

> Genutzt wird **Markdown** oder eine Markdown-ähnliche Syntax vorwiegend auf Entwicklerplattformen eher technikaffinem Publikum wie **GitHub**, Stack Overflow oder der Blogging-Plattform Ghost.

*Vor-* und *Nachteile* siehe : [Versionsverwaltung](#versionsverwaltung)

#### Lizenz

Auch auf der Plattform GitHub gibt es Lizenzen. Benutzer können aus bestimmten Lizenzen wählen, an die sich in weiterer Folge alle halten müssen.
Man kann sich mit einer Lizenz absichern (zB. Rechtsstreit).

--------------------------------------------

## Grundwissen in GitHub

* ### Überschriften
Man setzt ein **Doppelkreuz/Hash** vor die Überschrift.
In GitHub kann man bis zu 6 Hashes verwenden.

      # Überschrift
      ## Überschrift
      ###### Überschrift

* ### Fett
Vor und nach dem Wort zwei *.
    
      **Fett**
**Fett**

* ### Kursiv
Vor und nach dem Wort ein *.

      *Kursiv*
*Kursiv*

* ### Fett und Kursiv
Vor und nach dem Wort drei ***.

      ***FettKursiv***
***FettKursiv***

* ### Durchgestrichen
Vor und nach dem Wort zwei ~~.

      ~~Durchstreichen~~
~~Durchstreichen~~

* ### Hyperlink

      [Link](https://....)
[Link](https://de.wikipedia.org/wiki/Hyperlink)

* ### Bilder
      
      ![Bild](https://...)
![Bild](https://webserver.x-technik.com/upload/images/113087.jpg)

* ### Tabelle

      Einheit | Thema | Datum
      ------- | ----- | -----
      1 | Versionsverwaltung | 09.12.2019
      2 | Linux Grundlagen 1 | 16.12.2019

Einheit | Thema | Datum
------- | ----- | -----
1 | Versionsverwaltung | 09.12.2019
2 | Linux Grundlagen 1 | 16.12.201

* ### Listen
entweder mit Punkten oder automatischer Nummerierung.

      1) Wort
      1) Wort
  1) Wort
  1) Wort
      
* ### Programm
mit Highlighting
      
      ``` C
      int main() {
      printf("GitHub");
      return 0;
      }
      ```
``` C
int main() {
printf("GitHub");
return 0;
}
```

* ### Zitat
      
      > Zitat
> Zitat

* ### Abtrennung
Mehrmals Bindestrichtaste
      
      ---------------
---------------

* ### Hinterlegen
Zweimaliges drücken der Tabulatortaste

* ### Inhaltsverzeichnis

      [Inhaltsverzeichnis](#inhaltsverzeichnis)
[Inhaltsverzeichnis](#inhaltsverzeichnis)
