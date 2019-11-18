# Laborprotokoll  3AHME (2019/20)

* **Thema:** Versionsverwaltung
* **Datum:** 18.11.2019
* **Abwesend:** Keiner
* **Erstellt von:** Kogler Andreas

----------------------------------------------------------------------------------------------

## Inhaltsverzeichnis

1. [Versionsverwaltungssysteme](#versionsverwaltungssysteme)
2. [Github](github)
3. [Dokumentieren](dokumentieren)
4. [Markdown](markdown)
5. [Ebenen und Branches](ebenen-und-branches)
----------------------------------------------------------------------------------------------

## Versionsverwaltungssysteme

Ein Versionsverwaltungssystem dient zur Verwaltung von verschiedenen Versionen einer Repository. Dies läuft so ab, dass alle Versionen auf ein Repository, Datenbank, hochgeladen werden und diese Versionen immer aktualisiert werden.
Vorteile von einem solchem System sind:
* Wenn eine neue Version nicht funktioniert, kann man zur letzten stabilen wechseln
* man kann dadurch sehr gut im Team arbeiten
* und man hat einen Schutz vor sich selbst, angenommen man löscht versehentlich etwas raus, dann kann man das fehlende aus einer älteren Version holen

### Git
Git ist ein sogenanntes Versionsverwaltungssystem, welches von Linus Thorwald erschaffen wurde. Dies ist eine freie software.

Siehe [Wikipedia](https://de.wikipedia.org/wiki/Git).

Die Version kann man auf einem Linuxrechner mit dem command *git --version* anzeigen lassen.

## Github 
Github ist eine Web-Plattform für Git verwaltete Projekte, welche sehr erfolgreich war. Deshalb wurde sie von Microsoft gekauft.

### Grundlagen
Wenn man registriert ist kann man sich einloggen, indem man github.com/Benutzername hineinschreibt und dann seine E-Mail Adresse und sein Passwort eingibt.  
Ein neues Repository kann man unter dem Reiter Repository und dann New anlegen. Dann kann man den Namen, eine Programmiersprache und eine Lizens hinzufügen. Noch dazu haben wir ausgewählt, dass die Datenbank öffentlich ist, da eine Private kostenpflichtig ist. Weiters haben wir angekreuzt, eine readme Datei anzulegen.  
Danach waren drei Dateien angelegt, README.md, license und .gitignore. Darin kann man schreiben, die Lizens durchlesen und die Dateitypen sehen oder auch ändern, welche unterstützt werden.
  
  ## Dokumentieren
  ### handschriftlich 
  Vorteile:
 * flexibel
 * schnell
 
 Nachteile:
 * unleserlich
 * manchmal unübersichtlich
 * kein copy/paste
 * elektronisch unmöglich zu suchen
 
 ### Schreibmaschine
 Vorteile:
 * leserlich
 
 Nachteile:
 * kein ausbessern möglich
 
 ### Textverarbeitung
 Vorteile: 
 * leserlich
 * übersichtlich
 * veränderbar
 * elektronisch verarbeitbar
 
 Nachteile:
 * hoher Zeitbedarf
 
 ### Markdown
 Markdown kombiniert Vorteile vom handschriftlichen Dokumentieren und der Textverarbeitung.
 
 Vorteile:
 * schnell
 * einfach
 
 ## Markdown
laut [Wikipedia](https://de.wikipedia.org/wiki/Markdown)
>Markdown ist eine vereinfachte Auszeichnungssprache, die von John Gruber und Aaron Swartz entworfen und im Dezember 2004 mit Version 1.0.1 spezifiziert wurde.
 
 1. **Überschriften** schreibt man, indem man ein # vor dem Wort, dass die Überschrift sein soll, macht. Man kann auch Unterüberschriften machen. Dafür muss man 2 oder mehr Hashtags vor das Wort stellen. Maximal sind 6 möglich.
 1. **Zeilenumbruch:** Das erledigt man mit zwei Leerzeichen hintereinander.
 1. **Fett**, *Kursiv*, oder ***Fett und Kursiv*** macht man mit 2, 1, oder 3 Sternchen nach und vor dem Wort.
 1. **Liste :** Eine Liste kann man erstellen, wenn man untereinander die Zeilen mit einem Stern beginnt. Dies ist auch mit Auflistungen möglich also mit <Zahl>.
 1. **Tabellen :** 1. Zeile: Tabellenüberschrift | Tabellenüberschrift 2.Zeile : -------- | --------, in den weiteren Zeilen kann man den Inhalt eintragen
 1. **Links :** [angezeigter Name] (Link)
 1. **Bild :** ![angezeigter Name] (Link)
 1. **Programm** `main()`:

  ```C
  int main () {
  printf("Willkommen");
  return 0;
  }
   ```
 9. **Zitat :** Vor dem Zitat ein '>'  
 
Diese Befehle/Sachen findet man zusammengefasst [hier](https://github.com/mastering-markdown).

## Ebenen und Branches
Branches sind Verzweigungen. Es gibt einen masterbranch und weitere branches wie man in der Abbildung 1 sehen kann.
![Abbildung 1](https://camo.githubusercontent.com/fe7346b2099985eecb0aa828d84a84432187fbec/68747470733a2f2f6172636377696b692e7577796f2e6564752f696d616765732f312f31392f4769744875625f466c6f775f73746570732e706e67)



### Ebenen
Es gibt verschiedene Ebenen zwischen die man mit Hilfe von commands tauscht. Diese Ebenen werden in Abbildung 2 dargestellt.

![Abbildung 2](https://camo.githubusercontent.com/5a4967992d07a6f0f97422e6de4296edcbbe6050/68747470733a2f2f72656164736168696c2e66696c65732e776f726470726573732e636f6d2f323031362f30392f6769745f63686561745f73686565742e706e673f773d36333667)

Um zwischen diesen Ebenen switchen zu können werden folgende Befehle benötigt.
* git clone (link)
* ls
* cd [Verzeichnis]
* git status
* git checkout [branch]
* gedit []
* git add
* git commit 
* git push
