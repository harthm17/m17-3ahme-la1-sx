# 1. Protokoll
---------------------------------------------
## Thema: Versionsverwaltung und Markdown
---------------------------------------------
Datum:      18.11.2019  
Gruppe:     2  
Abwesend:   keiner  
Verfasser:  Thomas Harrer  
---------------------------------------------
## Inhaltsverzeichnis

1) [Versionsverwaltungssysteme](#versionsverwaltungssysteme)
  * [Definition](#definition)
  * [Vorteile](#vorteile)
  * [Nachteile](#nachteile)
  * [Git](#git)
2) [Github](#github)
  * [Was ist Github?](#was-ist-github)
  * [Grundlagen](#grundlagen)
3) [Dokumentieren](#dokumentieren)
  * [Arten von Dokumentation](#arten-von-dokumentieren)
4) [Markdown](#markdown)
  * [Formatierung](#formatierung)
5) [Ebenen und Branches](#ebenen-und-branches)
  * [Merge](#merge)
  * [Befehle](#befehle)
  
  
---------------------------------------------

## Versionsverwaltungssysteme

### Definition
Ein Versionsverwaltungssystem dient zur Verwaltung von verschiedenen Versionen einer Repository. Es funktioniert folgendermaßen, dass alle Versionen in einem Repository, Datenbank, gespeichert werden. Die Versionen werden immer hochgeladen undaktualisiert.

### Vorteile
  * Angenommen man hat bei der neuersten Version einen Fehler kann man ohne Probleme zur letzten stabilen Version wechseln.
  * Man kann von mehreren PCs darauf zugreifen -> **Teamworking** und **Ordnung**
  * Der Schutz vor sich selbst, angenommen man löscht etwas herraus, kann man in eine ältere Version gehen und diesen Teil wieder reinkopieren.

### Nachteile
  * man muss Besitz eines PCs sein -> Anschaffungskosten eines PCs
  * Solange man keine kostenplichtige Version benutzt, ist der Einblick in deine Daten jedem gewehrt.

### Git

Git ist ein Versionsverwaltungssystem, welches von Linus Thorwald entwickelt wurde. Ein großer Vorteil von Git ist, das es kostenlos ist.

Genaueres können sie unter [Wikepedia](https://de.wikipedia.org/wiki/Git) nachlesen.

Die aktuelle Version auf einem Linuxsystem mit diesem Befehl nachsehen.
```
  git --version
```

---------------------------------------------

## Github

### Was ist Github?

Laut [Wikepedia](https://de.wikipedia.org/wiki/GitHub):
> GitHub ist ein Onlinedienst, der Software-Entwicklungsprojekte auf seinen Servern bereitstellt (Filehosting). Namensgebend war das Versionsverwaltungssystem Git. Die GitHub, Inc. hat ihren Sitz in San Francisco in den USA. Ähnliche Dienste sind GitLab und Bitbucket.

Da Github einer so erfolgreiche Web-Plattform war, wurde sie von Mircosoft für 6,4 Milliarden Euro gekauft. Laut Mircosoft soll Github weiterhin eine unabhängige Plattform bleiben, ob diese Aussage richtig ist werden wir in Zukunft noch sehen.

### Grundlagen

Wenn man bereits registriert ist kann man sich einloggen indem man github.com/(benutzername) in seinem Browser eingibt, nach Aufruf muss man nur mehr seine E-Mail und sein Passwort eingeben.

Neue Repositories erstellt man in seinem Profil unter Reiter Repositories. Sie müssen auf New klicken und dann bekommen Sie die Möglichkeit den Namen, die Programmiersprache, die Liezenz hinzuzufügen. Dannach haben wir erfahren, dass unserer Datenbank öffentlich ist, da man sonst eine kostenpflichtige Version benötigt.
Nach der Erstellung waren 3 Dateien in unserer Datenbank, eine README.md, eine licens und eine .gitignore. In diesen Dateien kann man schreiben, die Liezenz durchlesen und auch die Datentypen sehen oder auch ändern, welche unterstützt werden.

**Liezenzen sind sehr wichtig, falls etwas passieren sollte, ist man schuldig!**

---------------------------------------------

## Dokumentieren

### Arten von Dokumentieren

* handschriftlich
  * Vorteile: 
     * flexibel
     * schnell
  * Nachteile:
     * unleserlich
     * Kopie ist sehr unständlich
     * unübersichtlich
     * kein copy paste
     * auf eine lange Zeit sehr mühsam
     * **nicht elektronisch suchbar**
  
* Schreibmaschine
  * Vorteile:
     * leserlich
  * Nachteile: 
     * sehr mühsam
  
* Textverarbeitung
  * Vorteile:
     * leserlich
     * übersichtlich
     * sehr leicht veränderbar
     * elektronisch verarbeitbar
     * **es ist elektronisch suchbar**
     * copy paste ist möglich
  * Nachteile:
     * Zeitbedarf ist höher
     
---------------------------------------------

## Markdown

Laut [Wikepedia](https://de.wikipedia.org/wiki/Markdown=:
> Markdown ist eine vereinfachte Auszeichnungssprache, die von John Gruber und Aaron Swartz entworfen und im Dezember 2004 mit Version 1.0.1 spezifiziert wurde. Ein Ziel von Markdown ist, dass schon die Ausgangsform ohne weitere Konvertierung leicht lesbar ist.

Markdown ist eine Mischung von handschriftlicher Dokumentation und einer Textverabeitung.

Markdown ist eine Textdatei keine Textverarbeitungsdatei.


### Formatierung

 * Überschriften:
 
 Überschriften sind möglich, indem man ein # setzt und dann nach einem Leerzeichen die Überschrift schreibt. Man kann biszu 6# verwenden, je mehr # desto kleiner wird die Überschrift.
 ```
   # Überschrift
 ```
 
 * Zeilenumbruch
 
 Man kann einen gezielten Zeilenumbruch machen indem man einfach 2 Leerzeichen hintereinander setzt.
 
 * Schriftarten
 
 Es gibt auch **fette**, *kursive* Schrift, aber es gibt auch ***beides*** in einem.
 
 ```
   * Text *     <- kursiv
   ** Text **   <- fett
   *** Text *** <- fett und kursiv
 ```
 
 * Nummerierung
 
 Einfach die Zahl eingeben mit einem Punkt aufhören. Nach einem Leerzeichen kann man die Aufzählung beginnen.  
 **Man kann durchgehend die gleiche Zahl verwenden, es wird richtig gestellt.**
 
 * Liste
 
    * handschriftlich dokumentieren
      * Vorteile:
        * ...
        * ...
 
 ```
   * handschriftlich dokumentieren
     * Vorteil:
       * ...
       * ...
 ```
 
 * Tabellen
 
 
  Katalognummer | Name 
  ------------- | ------
  1 | Adam  
  2 | Augustin  
  3 | Danko  
 
 ```
  Katalognummer | Name
  ------------- | ------
  1 | Adam
  2 | Augustin
  3 | Danko
 ```
 
 * Links
 
 Man kann ganz einfach Links einbeziehen, man muss einfach auf den blauen Text klicken und schon öffnet sich der Link, jedoch ist es empfehlenswert denn Link in einem neuen Tab zu öffnen.
 
 Siehe [Github-Mastering Markdown](https://guides.github.com/features/mastering-markdown/)
 
 ```
  Siehe [Name](Link)
 ```
 
 * Bilder
 
 ![Bild](http://www.htl-kaindorf.at/images/plg_jdvthumbs/thumb-mecha3-c9a0320c773679a5e61870cd3180761a@2x.jpg)
 
 ```
  ![Bild](link)
 ```
 
 * Quelltexte
 
 Man kann sehr leicht Quelltexte hervorheben.
 
 ```
 C
  int main() {
      printf("Hello World!\n");
      return 0;
  }   
  ```
  
  ```
       ``` C
      int main() {
          printf("Hello World!\n");
          return 0;
      }   
      ```
  ```
  
 * Zitate
 
Laut Wikepedia(https://de.wikipedia.org/wiki/Zitat):
> Ein Zitat (das, lateinisch citatum „Angeführtes, Aufgerufenes“ zu lat. citāre „in Bewegung setzen, vorladen“, vgl. „jemanden vor Gericht zitieren“[1][2]) ist eine wörtlich oder inhaltlich übernommene Stelle aus einem Text oder ein Hinweis auf eine bestimmte Textstelle. Auch andere Medien, wie Bilder und Musik, können als Zitat verwendet werden.

``` 
[Quelle]:
> Zitat
```

* Abteilung durch Strich

Abschnitt 1 
------------------------------------------
Abschnitt 2

```
Abschnitt 1 
------------------------------------------
Abschnitt 2
```

* Inhaltsverzeichnis

Der Vorteil an solchen Inhaltsverzeichnissen ist, wenn man auf den Punkt Markdown klickt, wird sofort zu diesem Abschnitt gesprungen

Inhaltsverzeichnis
   * [Markdown](#markdown)
   * [Ebenen und Branches](#ebenen-und-branches)

``` 
Inhaltsverzeichnis
   * [Markdown](#markdown)
   * [Ebenen und Branches](#ebenen-und-branches)
```

 ---------------------------------------------

## Ebenen und Branches

Schnell gesagt sind Branches Verzweigungen.

Es gibt einen masterbranch, möchte man jedoch nicht auf diesen arbeiten, erstellt man sich einen Nebenbranch. Diese kann man später wieder ohne Probleme zusammenfügen. Wie sie in der kommenden Abbildung sehen können.

![branches](https://camo.githubusercontent.com/fe7346b2099985eecb0aa828d84a84432187fbec/68747470733a2f2f6172636377696b692e7577796f2e6564752f696d616765732f312f31392f4769744875625f466c6f775f73746570732e706e67)


Es gibt verschiedene Ebenen. Man kann mit Hilfe von commands diese wechseln. Wie sie in der kommenden Abbildung sehen können.

![git](https://www.stephenmarron.com/wp-content/uploads/2017/02/git.png)


### Merge

Merge bedeutet, dass 2 Änderungen wieder zusammen gefügt werden.

### Befehle

* Grundlegende Befehle

   * ls -l = abgelegte Dateien
   * cd (Verzeichnissname) = in ein anderes Verzeichniss kommen

* commands für Git   
   * gitclone (link) = kopiert einen Link
   * git status = zeigt die Änderungen der Datei an
   * git checkout (Benutzername) = man wählt den Branch aus
   * gedit (Dateiname) = öffnet die Datei
   * git add (Dateiname) = damit gibt man bekannt, dass die Datei verändert wurde
   * git commid -m "Update (Dateiname)" = Änderungen werdedn lokal gespeichert
   * git push = sendet die Änderungen zum masterbranch (beim ersten mal muss man sich mit seinen Anmeldedaten von Github anmelden)
   * git merge = einen anderen Branch neben deinen aktiven hinzufügen
   
Um eine Datei hochzuladen braucht man folgende Reihenfolge:
   * gitclone
   * ls
   * cd 
   * git status
   * gitcheckout
   * gedit
   * git add
   * git commid
   * git push
