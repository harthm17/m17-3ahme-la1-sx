# Protokoll 1 Labor/SX 3AHME (2019/20)

------------------------------------------------------------

* **Thema:** Versionsverwaltung
* **Datum:** 18.11.2019
* **Gefehlt:** -
* **Erstellt von:** Haring Stefan (harstm17)
* **Protokoll letzte Einheit:**
* **Protokoll nächste Einheit:**

------------------------------------------------------------

## Inhaltsverzeichnis
1. [Themen der Einheiten](#themen-der-einheit)
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

----------------------------------------------------------------

### Themen der Einheiten
1. Einheit: Versionsverwaltung, Markdown, Git, Github (Protokoll benötigt)
1. Einheit: Linux Grundlagen Teil 1
1. Einheit: Test, Linux Grundlagen Teil 2 (Protokoll benötigt)

----------------------------------------------------------------------

### Versionsverwaltung
* #### Definition:
[Wikipedia](https://de.wikipedia.org/wiki/Versionsverwaltung) definiert folgendes:
>Eine Versionsverwaltung ist ein System, das zur Erfassung von Änderungen an Dokumenten oder Dateien verwendet wird. Alle Versionen werden in einem Archiv mit Zeitstempel und Benutzerkennung gesichert und können später wiederhergestellt werden. Versionsverwaltungssysteme werden typischerweise in der Softwareentwicklung eingesetzt, um Quelltexte zu verwalten. Versionsverwaltung kommt auch bei Büroanwendungen oder Content-Management-Systemen zum Einsatz.
>Eigene Definition: Unter Versionsverwaltung versteht man, das Speichern von Daten in einer Datenbank unter verschiedenen Versionen.

* #### Vorteile:
1. Rückgriff auf die Vorgängerversion aufgrund von Fehler in der neuen Version
1. Teamworking möglich
1. auch über das Netzwerk abrufbar
1. man kann genau nachweisen, wer welche Fehler gemacht hat
1. auch nach dem irrtümlichen Löschen von Daten, kann man wieder auf sie zugreifen
    
 * #### Nachteile:
1. hohe Anschaffungskosten (besorgen eines PC´s)
1. ohne Anschaffung der kostenpflichtigen Version, ist der Einblick in Daten jedem gewehrt

--------------------------------------------------------------------------------------------------

### Dokumentieren
#### Arten:
##### handschriftlich:
* **Vorteile-->** flexibel, schnell
* **Nachteile-->** unleserlich, Kopie umständlich, manchmal unübersichtlich, schnelles Suchen von Daten nicht möglich, nur temporär nützlich
                              
##### Schreibmaschine:
(nicht relevant, da diese Art der Dokumentierung nur mehr selten bis gar nicht mehr auftritt)
      
##### Textverarbeitung:
* **Vorteile-->** leserlich, übersichtlich, veränderbar, einfache Suche, copy-paste möglich
* **Nachteile-->** teilweise sehr umstädnlich, Zeitbedarf hoch 
                               
---------------------------------------------------------------------------------------------------------------------------------

### Markdown
*Was ist Markdown?*
* Laut [Wikipedia](https://de.wikipedia.org/wiki/Markdown):
>Markdown ist eine vereinfachte Auszeichnungssprache, die von John Gruber und Aaron Swartz entworfen und im Dezember 2004 mit Version 1.0.1 spezifiziert wurde. Ein Ziel von Markdown ist, dass schon die Ausgangsform ohne weitere Konvertierung leicht lesbar ist. Als Auszeichnungselemente wurden daher vor allem Auszeichnungsarten verwendet, die in Plain text und E-Mails üblich sind. Auch andere Auszeichnungssprachen mit ähnlichen Zielen zur Lesbarkeit hatten Einfluss auf die Syntax.

* Eigendefinition:
>Markdown ist die Mischung von der Handschriftdokumentation und der Textverarbeitung. Hierbei werden die Vorteile beider Techniken genutzt.

Die Syntax von [Markdown](https://de.wikipedia.org/wiki/Markdown) wird vor allem auf Entwicklerplattformen verwendet. (z.B. GitHub)
Die Dateiendung ist meist **.md** oder **.markdown** .

----------------------------------------------------------------------------------------------------------------------------------------

### GitHub
[GitHub](https://de.wikipedia.org/wiki/GitHub) ist eine Web-Plattform für Git verwaltete Projekte. Github ist die ideale Open Source Software in Sachen [Versionsverwaltungssysteme](https://de.wikipedia.org/wiki/Versionsverwaltung).

##### Vorteile
1. man verliert nur sehr schwer Daten und Mitschriften
1. mit ein bisschen Übung ist es sehr leicht zu bedienen
1. es eignet sich sehr gut für Gruppenarbeiten da jeder den Arbeitsstand und Daten vom anderen sehen kann
1. Es ist kostenlos (außer man will seine Daten nicht veröffentlichen)
1. man hat die Möglichkeit alles in einer übersichtlichen und nachvollziehbaren Form zu machen
1. es geht sehr schnell
1. es kann keiner was stehlen, da es sowieso schon öffentlich ist
1. es kann kein anderer ein Patent auf deine hochgeladenen Sachen anmelden (solange man die Rechte richtig einschränkt)
1. andere könnten Fehler entdecken und dich darauf hinweisen

##### Nachteile
1. man benötigt einen PC (Kosten)
2. man kann keine neuen Erfindungen oder Entwicklungsstände dokumentieren, da es andere sehen können
      
##### Grundkenntnisse

* **Lizenz**

Die Lizenz spielt eine große Rolle in Sachen Rechtslage.


* **Computersprache:**

    ```C
    int main () 
    {
    printf("Hallo");
    return 0;
    }
    ```

* **Überschriften:** ( je mehr # desto kleiner wird die Überschrift)
            
      #Ü1
      ##Ü2
      ###Ü3
      ####Ü4
      ....(max 6#)

* **etwas Nummerieren** (Nummerierung passt sich selbst auf 1,2,3... an)
                        (*Vorteil:* falls man eine Nummerierung später hinzufügen möchte,
                         muss man nicht alle nachfolgenden Nummerierungen wieder ausbessern)
```
1. A
1. B
1. C
```

* **etwas verlinken:** 
```
[Name](link)
```

* **etwas durchstreichen:**
```
~~Wort~~
```

* **etwas kursiv stellen:**
```
*Wort*
```
* **Liste erstellen:** 
```
     *text
     *text
     *text
   
     1.
     1.
     1.
```
* **etwas fett machen:**
```
**Wort**
```

* **etwas zitieren:**
```
>Zitat
```

* **grau hinterlegen:** 
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

* **Einfügen von Bildern**
```
![](adresse des bildes) eingefügt.
```
*Beispiel:* Quelle: https://webserver.x-technik.com/upload/images/113087.jpg
![](https://webserver.x-technik.com/upload/images/113087.jpg)



* **Abteilung durch einen Strich kennzeichnen:** 
(einfach die Minustaste länger gedrückt halten)
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
Quelle: https://www.stephenmarron.com/wp-content/uploads/2017/02/git.png
![Git data transport](https://www.stephenmarron.com/wp-content/uploads/2017/02/git.png)

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
* git clone = damit kann man eine Kopie vom local repository machen
```
Terminal eingabe: zum clonen der Datei: git clone https://github.com/<Autor>/<Datei>
                           ins richtige Verzeichniss: cd <Datei>
                           die Datei öffnen: gedit README.md
                           Microsft Visual Studio: code ~/<Datei>/README.md
```
* git add = damit sagt man, dass eine Datei geändert wurde.
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
