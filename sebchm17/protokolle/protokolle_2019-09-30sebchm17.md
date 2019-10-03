# Protokoll Labor/SX 3AHME (2019/20)

* **Thema** Git, Linux
* **Datum** 30.09.2019
* **Gefehlt** Niemand
* **Protokoll letzte Einheit**
* **Protokoll Nächste Einheit**
-----------------------------------------------------------------------------------------------------------------------------------
## Inhaltsverzeichnis
1. [Einführung Github](#einführung-github)
   * [Überschriften](#überschriften)
   * [Zitate](#zitate)
   * [Markdown](#markdown)
   * [Inhaltsverzeichnis erstellen](#inhaltsverzeichnis-erstellen)
   * [Text Grau hinterlegen](#text-grau-hinterlegen)
   * [Fett/Kursiv schreiben](#fett/kursiv-schrieben)
   * [Liste/Aufzählungen erstellen](#liste/aufzühlungen-erstellen)
   * [Code](#code)
2. [Git](#git)
3. [Shell Kommandos](#shell-kommandos)
4. [Branch](#branch)
5. [Merge](#merge)

-----------------------------------------------------------------------------------------------------------------------------------
## Einführung Github
Github ist ein Versionsverwaltungssystem und der Zweck ist, dass Dokumente nicht so einfach verschwinden. Natürlich wird jede Änderung an Dokumenten genau aufgezeichnet. Solche Versionsverwaltungssysteme ist die Vorraussetzung für eine gute Gruppenarbeit. Am Anfang ist es wichtig sich rechtlich mit einer Liecense abzusichern, da diese Datei ein jeder lesen kann.
Github kostet erst etwas wenn die Dokumente privat bleiben sollen.
  
### Überschriften

    #h1     größte Überschrift
    ##h2
    ###h3
    ####h4
    #####h5
    ######h6

Es können bis zu 6 verschidene Überschriften gewählt werden indem man ein hash davor setzt.

### Zitate

In Markdown kann man kopierte Texte als Zitat kennzeichnen.

      > Beispiel
      
### Inhaltsverzeichnis erstellen
Bei der Erstellung eines Inhaltsverzeichnis in Markdown setzt man die einzelnen Überschriften in Eckige Klammern. Wenn man die Überschrift so hervorheben möchte das sie so aussieht wie ein Link muss man dahinter in runden Klammern die Überschrift nochmal mit einem Hashtag davor nochmals schreiben.
  
      [Beispiel Verzeichnis](#beispiel-verzeichnis)
### Text Grau hinterlegen
In Markdown kann man den Text grau hinterlegen indem 2 mal die Tabolator-Taste gedrückt wird.

    beispiel

### Fett/Kursiv schreiben

    fett schreiben **......**
    kursiv schreiben *......*
    durchgestrichen ~~.....~~
    fett und kursiv ***...***

In Markdown gibst es 4 unterschiedliche Arten wie man etwas hervorheben kann.


### Markdown

Aus [Wikipedia][https://de.wikipedia.org/wiki/Markdown]
>Markdown ist eine vereinfachte Auszeichnungssprache, die von John Gruber und Aaron Swartz entworfen und im Dezember 2004 mit Version 1.0.1 spezifiziert wurde. Ein Ziel von Markdown ist, dass schon die Ausgangsform ohne weitere Konvertierung leicht lesbar ist. Als Auszeichnungselemente wurden daher vor allem Auszeichnungsarten verwendet, die in Plain text und E-Mails üblich sind. Auch andere Auszeichnungssprachen mit ähnlichen Zielen zur Lesbarkeit – wie reStructuredText oder Textile – hatten Einfluss auf die Syntax.

### Liste/ Aufzählungen erstellen

    * Beispiel 1
    * Beispiel 2
    * Beispiel 3

oder 

    1. Beispiel
    2. Beispiel
    3. Beispiel
    
Markdown zählt automatisch mit.
### Code

```bash
int main () {
  printf("Hallo");
  return 0;
  }
```
In Markdown kann man auch eine Programmiersprache kenzeichnen.

--------------------------------------------------------------------------------------------------------------------------------
# Git

![Git-Data Trasport][Git-Data Trasport]
https://www.patrickzahnd.ch/uploads/git-transport-v1.png

#### Stash

Beim Stash werden die Änderungen versteckt.

#### Workplace

***workspace*** bedeuted im deutschen Arbeitskopie und dort sind die repositories gespeichert.

#### Index

Hier befindet sich jene Datei, die als nächste commited wird.

#### Local Repository

In diesem Repository sind die lokalen Änderungen gespeichert. Diese Änderungen befinden sich am eigenen Rechner. 

#### Remote Repository

Repository auf dem Server (NICHT LOKAL)

```git add```

Dieser Befehl fügt eien Änderung in das Arbeitsverzeichnis hinzu.

```git commit```

Dieser Befehl erfasst einen Schnappschuss der eigenen bereitgestelten Änderung des Projekts.

```git reset```

Der Befehl löscht alle letzten Änderungen.

```git reset--hard```

Mit diesem Befehl löscht alle nicht festgeschriebenen Änderungen.

```git status```

Mit diesem Befehl kann man den aktuellen status abfragen. Man kann sehen welche Änderungen gespeichert wurden.

```git push```

Der Befehl ist für das hochladen vom lokalen repository in das remote repository zuständig. Dabei wird im terminal eine Benutzer und Passwort abfrage durchgeführt.

--------------------------------------------------------------------------------------------------------------------------------

# Shell Komandos

Jedes Betriebssystem hat seine eigene Eingabekonsole. Bei Linux hat sie den Namen Shell und man kann sher viel mit ihr machen.

Mit ``ls       list directory content`` gibt man dateien und verzeichnisse aus.
Mit ``cd       change directory ``wechselt man in ein andreres Verzeichnis.
Mit ``gedit`` kann man Textdateien bearbeiten.


--------------------------------------------------------------------------------------------------------------------------------
# Branch
![Branch][Branch]
Quelle:https://www.patrickzahnd.ch/uploads/gitflow.png




Ein Branch in Git ist nichts anderes als ein simpler Zeiger auf Commits.
Der Standardname eines Branches lautet master. 
Mit jedem Commit bewegt sich branch automatisch vorwärts.

--------------------------------------------------------------------------------------------------------------------------------

# Merge

Beim Merging(Zusammenführen) werden die verschiedenen commit's zum Ziel branch zusammengeschmolzen.

--------------------------------------------------------------------------------------------------------------------------------
[Git-Data Trasport]:https://www.patrickzahnd.ch/uploads/git-transport-v1.png
[Branch]:https://www.patrickzahnd.ch/uploads/gitflow.png


