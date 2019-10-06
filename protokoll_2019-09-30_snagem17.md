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
* Quelle:[Wiki](https://de.wikipedia.org/wiki/Markdown)
>Markdown ist eine vereinfachte Auszeichnungssprache, die von John Gruber und Aaron Swartz entworfen und im Dezember 2004 mit Version 1.0.1 spezifiziert wurde. Ein Ziel von Markdown ist, dass schon die Ausgangsform ohne weitere Konvertierung leicht lesbar ist. Als Auszeichnungselemente wurden daher vor allem Auszeichnungsarten verwendet, die in Plain text und E-Mails üblich sind. Auch andere Auszeichnungssprachen mit ähnlichen Zielen zur Lesbarkeit hatten Einfluss auf die Syntax.

Die Syntax von [Markdown](https://de.wikipedia.org/wiki/Markdown) oder wird vor allem auf Entwicklerplattformen verwendet. (z.B. GitHub)
Die Extension ist meist **.md** oder **.markdown**.

#### 2Bsp zur Weiterentwicklung von Markdown
* [Common Mark](https://de.wikipedia.org/wiki/CommonMark): ist eine vereinfachte Aufzeichnungssprache. Unterschiede zu Markdown findet man z.B. bei Verschachtelten Aufzählungen oder bei Blöcken, da bei Common Mark durch ein Leerzeichen der Block beendet wird was bei Markdown nicht der Fall ist.
* GitHub Flavored Markdown: ist eine Erweiterung die auf Common Mark aufgebaut ist. Es erweitert die Syntax.



### GitHub
[GitHub](https://de.wikipedia.org/wiki/GitHub) ist ein [Versionsverwaltungssystem](https://de.wikipedia.org/wiki/Versionsverwaltung)

#### Vorteile
      1. man verliert nur sehr schwer Daten und Mitschriften
      2. mit ein bisschen Übung ist es sehr leicht zu bedienen

#### Nachteile
      1. man benötigt einen PC (Kosten)
      2. 
#### Grundkenntnisse

* **Computersprache:**

    ```C
    int main () 
    {
    printf("Hallo");
    return 0;
    }
    ```

* **Überschriften:**
            

* **etwas verlinken:** 
```
[Name](Link)
```

* **etwas durchstreichen:**
```
~~Wort~~
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
[Merge](https://de.wikipedia.org/wiki/Merge) bedeutet, dass 2 Änderungen zusammengeführt werden. Das ist ein oft verwendeter Vorgang bei Versionsverwaltungssystemen.

Quelle:[wiki](https://de.wikipedia.org/wiki/Merge)
>Merge ist der Vorgang des Abgleichens mehrerer Änderungen, die an verschiedenen Versionen derselben Datei getätigt wurden. Das Zusammenführen verschiedener Datei-Versionen ist ein zentraler Vorgang bei den meisten Versionsverwaltungssystemen, weshalb diese meist unterschiedliche Merge-Algorithmen unterstützen. Viele Versionsverwaltungssysteme werden zudem mit grafischen Hilfsprogrammen ausgeliefert, die das Mergen vereinfachen sollen.
