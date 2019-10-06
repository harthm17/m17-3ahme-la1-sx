# Protokoll Labor/SX 3AHME (2019/20)

* **Thema:** Markdown,GitHub,Git
* **Datum:** 30.09.2019
* **Gefehlt:** Niemand
* **Erstellt von:** Georg Schnabel

## Inhaltsverzeichnis
1. [Markdown](https://de.wikipedia.org/wiki/Markdown)
    * Weiterentwicklung von Markdown
2. [GitHub](https://de.wikipedia.org/wiki/GitHub)
    * Grundkenntnisse
3. [Git](https://de.wikipedia.org/wiki/Git)
    * local/remote repository
    * Kommandos für das Terminal
    * Kommandos für Git
4. [Merge](https://de.wikipedia.org/wiki/Merge)    

### Markdown
Was ist Markdown?
* [Markdown](https://de.wikipedia.org/wiki/Markdown)
>Markdown ist eine vereinfachte Auszeichnungssprache, die von John Gruber und Aaron Swartz entworfen und im Dezember 2004 mit Version 1.0.1 spezifiziert wurde. Ein Ziel von Markdown ist, dass schon die Ausgangsform ohne weitere Konvertierung leicht lesbar ist. Als Auszeichnungselemente wurden daher vor allem Auszeichnungsarten verwendet, die in Plain text und E-Mails üblich sind. Auch andere Auszeichnungssprachen mit ähnlichen Zielen zur Lesbarkeit hatten Einfluss auf die Syntax.

Die Syntax von Markdown oder wird vor allem auf Entwicklerplattformen verwendet. (z.B. GitHub)
Die Extension ist meist **.md** oder **.markdown**.

#### 2Bsp zur Weiterentwicklung von Markdown
* [Common Mark](https://de.wikipedia.org/wiki/CommonMark): ist eine vereinfachte Aufzeichnungssprache. Unterschiede zu Markdown findet man z.B. bei Verschachtelten Aufzählungen oder bei Blöcken, da bei Common Mark durch ein Leerzeichen der Block beendet wird was bei Markdown nicht der Fall ist.
* GitHub Flavored Markdown: ist eine Erweiterung die auf Common Mark aufgebaut ist. Es erweitert die Syntax.



### GitHub
[GitHub](https://de.wikipedia.org/wiki/GitHub) ist ein [Versionsverwaltungssystem](https://de.wikipedia.org/wiki/Versionsverwaltung) und ist dazu gedacht keine Daten, Mitschriften zu verlieren. Dient aber auch sehr gut für Projektarbeiten da die Aufzeichnungen der anderen Gruppenmitglieder zugänglich sind. Ein dadurch entstandener Nachteil ist, dass man keine Erfindungen und Entwicklungsprozesse mit GitHub dokumentieren soll da jemand anders die Daten lesen könnte.

#### Grundkenntnisse

* **Überschriften:**
      #Ü1
      ##Ü2
      ###Ü3
      ....(bis 6# möglich)

* **etwas verlinken:** 
```
[Name](Link)
```

* **etwas kursiv stellen:**
```
*Wort*
```
* **etwas fett machen:**
```
**Wort**
```

* **etwas zitieren:**
```
>Zitat
```

* **grau hinterlegen:** 2mal Tabulatortaste

### Git

![Git data transport](https://www.stephenmarron.com/wp-content/uploads/2017/02/git.png)

Quelle:[Wiki](https://de.wikipedia.org/wiki/Git)
>Git ist eine freie Software zur verteilten Versionsverwaltung von Dateien, die durch Linus Torvalds initiiert wurde. 

Als Editor wird [gedit](https://de.wikipedia.org/wiki/Gedit) verwendet. Es wird zwischen remote repository und local repository unterschieden.

#### local/remote repository

* local repository = sind die lokalen Änderungen
* remote repository = sind an einem z.B. Server gespeichert der nicht lokal ist

#### Kommandos für das Terminal:
* history = man sieht welche Kommandos man schon verwendet hat.
* reset = löscht den Bildschirm
* strg + = man vergrößert die Schrift
* strg - = man verkleinert die Schrift
* ALT = man macht die Menüleiste sichtbar
* exit = damit schließt man, um auch nachher auf die history zurückgreifen zu können

#### Kommandos für Git:
* git clone = damit kann man eine Kopie vom local repository machen
* git add = damit sagt man, dass eine Datei geändert wurde.
* git commit = dort muss immer stehen wer du bist, Änderungen werden lokal gespeichert
* git push = sendet die Veränderungen an den master branch
* git Status = zeigt die files wo etwas verändert wurde
* git reset = man macht lokale Veränderungen

### Merge:
Es werden 2 Änderungen zusammengeführt. Das ist ein oft verwendeter Vorgang bei Versionsverwaltungssystemen.
