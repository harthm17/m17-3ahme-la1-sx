# Labor-Protokoll

--------------------------------------------------------------

* **Thema:** Versionsverwaltung
* **Datum:** 09.12.2019
* **Gefehlt:** -
* **Erstellt von:** Thomas Pust (pusthy16)
* **Protokoll letzte Einheit:**
* **Protokoll nächste Einheit:**

--------------------------------------------------------------

## Inhaltsverzeichnis
1. [Themen der Laboreinheiten](#themen-der-labroeinnheit)
1. [Versionsverwaltung](#versionsverwaltung)
    * [Definition](#definition)
    * [Vorteile](#vorteile)
    * [Nachteile](#nachteile)
1. [Dokumentieren](#dokumentieren)
    * [Arten](#arten)
1. [Markdown](markdown)
1. [GitHub](github)
    * [Vorteile](#vorteile)
    * [Nachteile](#nachteile)
    * [Grundkenntnisse](grundkenntnisse)
1. [Git](#git)
    * [local/remote repository & stash](#local/remote-repository-&-stash)
    * [Grundlegendes](#grundlegendes)
    * [Kommandos für das Terminal](#kommandos-für-das-Terminal)
    * [Kommandos für Git](#Kommandos-für-Git)
1. [Branch](#branch)

---------------------------------------------------------------------------

### Themen der Laboreinheiten
1. Einheit: Versionsverwaltung und Dokumentation mit Markdown (Protokoll benötigt)
2. Linux Grundlagen Teil 1 (PLF)
3. Linux Grundlagen Teil 2 (Protokoll benötigt)

-------------------------------------------------------------------------------------

### Versionsverwaltung
* #### Definition:
[Wikipedia](https://de.wikipedia.org/wiki/Versionsverwaltung)
>Eine Versionsverwaltung ist ein System, das zur Erfassung von Änderungen an Dokumenten oder Dateien verwendet wird. Alle Versionen werden in einem Archiv mit Zeitstempel und Benutzerkennung gesichert und können später wiederhergestellt werden. Versionsverwaltungssysteme werden typischerweise in der Softwareentwicklung eingesetzt, um Quelltexte zu verwalten. Versionsverwaltung kommt auch bei Büroanwendungen oder Content-Management-Systemen zum Einsatz.
>wird auch manchmal Code Verions System (CVS) genannt

* #### Vorteile:
1. Zugriff auf alle bisherigen Versionen / Varianten --> es geht nichts verloren
1. Grundlage für Teamworking
1. Schutz vor sich selbst

* #### Nachteile:
1. Umgang muss erlernt werden

------------------------------------------------------------------------------------------------------------------------------------

### Dokumentieren
#### Arten:
##### Handschrif:
* **Vorteile-->** schnell, oft verfügbar, flexibel
* **Nachteile-->** manchmal unleserlich, Verbreitung schwierig, kein Backup,  nicht elektronisch verarbeitbar
                              
#### Bild erstellen:
* **Vorteile-->** schnell, gut zu verarbeiten, Backup
* **Nachteile-->** elektronisch nicht verarbeitbar, viel Speicherplatz erforderlich

##### Textverarbeitung:
* **Vorteile-->** leserlich, übersichtlich, veränderbar, einfach
* **Nachteile-->** zeitaufwändig

--------------------------------------------------------------------------------------------------------------------------------------

### Markdown
*Was ist Markdown?*
[Wikipedia](https://de.wikipedia.org/wiki/Markdown):
>Markdown ist eine vereinfachte Auszeichnungssprache, die von John Gruber und Aaron Swartz entworfen und im Dezember 2004 mit Version 1.0.1 spezifiziert wurde. Ein Ziel von Markdown ist, dass schon die Ausgangsform ohne weitere Konvertierung leicht lesbar ist. Als Auszeichnungselemente wurden daher vor allem Auszeichnungsarten verwendet, die in Plain text und E-Mails üblich sind. Auch andere Auszeichnungssprachen mit ähnlichen Zielen zur Lesbarkeit hatten Einfluss auf die Syntax.

-------------------------------------------------------------------------------------------------------------------------------------

### GitHub
[GitHub](https://de.wikipedia.org/wiki/GitHub) ist eine Web-Plattform für Git verwaltete Projekte.

##### Vorteile
1. Daten gehen schwert verloren
1. Teamworking
1. kostenlos

#### Nachteile
1. PC benötigt

#### Grundkenntnisse

* **Lizenz**

Mit einer Lizenz kann man Rechtsstreitigkeiten aus der Welt schaffen. (zB. MIT_License)

* **Quelltext:**

  ```C
    int main (){
    printf("Test");
    return 0;
    }
  ```
  
* **Überschriften**

>(mit ##...Unterüberschriften...max. 6#)
      #Test1
      ##Test2
      ###Test3
      ....

* **Listen**
```
* Test1     
* Test2     
* Test2     

1) Test1
2) Test2
3) Test3
```

* **fett**
```
**Wort**
```

* **zitieren:**
```
>Zitat
```

* **grau erlegen:** 
```
Zweimaliges Drücken der Tabulatortaste.
```

* **Inhaltsverzeichnis:** 
```
    [Überschrift](#überschrift)
```

* **Programm einfügen**
```
( ´´´(Programiersprache) Programm... ´´´) 

```

* **Bildern einfügen**
```
![](adresse des bildes) eingefügt.
```
*Beispiel:* Quelle: https://webserver.x-technik.com/upload/images/113087.jpg
![](https://webserver.x-technik.com/upload/images/113087.jpg)



* **Abteilung durch einen Strich kennzeichnen:** 
(Minustaste länger gedrückt halten)
```
----------------------------------------------------------------------------------------------
```

* **Tabelle erstellen:**
```
Version    | Name       | Datum
-----------|------------|------------
V 1.0      | Protokoll.docx | 18.11.2019

```
------------------------------------------------------------------------------------------------

### Git

Quelle:[Wiki](https://de.wikipedia.org/wiki/Git)
>Git ist eine freie Software zur verteilten Versionsverwaltung von Dateien, die durch Linus Torvalds initiiert wurde.

Als Editor wird [gedit](https://de.wikipedia.org/wiki/Gedit) verwendet. Es wird zwischen remote repository und local repository unterschieden. Es ist auch Offline zugänglich.

#### local/remote repository & stash

* local repository = sind die lokalen Änderungen
* remote repository = sind zB. an einem Server gespeichert, der nicht lokal ist
* stash: Zwischenspeicher für Änderungen

#### Grundlegendes
   Man kann sich die eigenen Daten von Github auf seinen eigenen Rechner clonen.
   Die Daten kann man dann am eigenen Rechner im Terminal bearbeiten.
   Nachdem man sie bearbeitet hat kann man sie wieder hochladen.
   Bei einem Projekt mit mehreren Leuten ist es gut wenn sich ein jeder die Daten clonen würde da es sicherer ist.
   
#### Kommandos für das Terminal:
* history = man sieht welche Kommandos man schon verwendet hat.
* reset = löscht den Bildschirm
* strg + = man vergrößert die Schrift
* strg - = man verkleinert die Schrift
* strg l = Bildschirm wird nach oben geschoben
* ls -l = abgelegte Dateien
* ALT = man macht die Menüleiste sichtbar
* Pfeil nach oben oder !<Befehl> = Kommandos können wiederholt werden
* cd <Verzeichniss> = in ein anderes Verzeichniss kommen
* exit = damit schließt man, um auch nachher auf die history zurückgreifen zu können

#### Kommandos für Git:
* git clone =  Kopie vom local repository 
```
Terminal eingabe: zum clonen der Datei: git clone https://github.com/<Autor>/<Datei>
                           ins richtige Verzeichniss: cd <Datei>
                           die Datei öffnen: gedit README.md
                           Microsft Visual Studio: code ~/<Datei>/README.md
```
* git add = Datei wurde geändert
```
Datei zurück auf den Server bringen
  
         Terminal eingabe: git add README.md          //Wenn man alles hinzufügen will dann: git add -A
                           git status
                           git commit -m "Update README.md"
                           Eingabe des Benutzers damit der Rechner weiß wer man ist: git config --global user.email "<Email>"
                                                                                     git config --global user.name "<Name>"
                           git commit -m "Update README.md"
                           git push
                           Dann muss man noch Benutzername und Passwort eingeben
```
* git commit = dort muss immer stehen wer du bist, Änderungen werden lokal gespeichert
* git push = sendet die Veränderungen an den master branch
* git status = zeigt die files wo etwas verändert wurde
* git reset = man macht lokale Veränderungen
* git merge = einen anderen Branch zu deinem aktiven Branch hinzufügen

-----------------------------------------------------------------------------------------------------------

### Branch (Ast)
Der Master [Branch](https://git-scm.com/book/en/v1/Git-Branching-What-a-Branch-Is) ist der Hauptast, wenn man nicht im Master Branch arbeiten will, macht man sich einen Nebenbranch, danach kann man den Nebenbranch wieder in den Master Branch zurück bringen.
