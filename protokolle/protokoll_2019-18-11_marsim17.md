# Protokoll LA1/SX 3AHME (2019/20)

* **Thema:** Versionsverwaltungssysteme, git, Github, Markdown
* **Datum:** 18.11.2019
* **Gefehlt:** -
* **Erstellt von:** Marcher Simon
* **Protokoll nächste Einheit:** [Protokoll 25.11.2019](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/marsim17/protokolle/protokoll_2019-25-11_marsim17.md)
---------
## Inhaltsverzeichnis

[Versionsverwaltungssysteme](#versionsverwaltungssysteme)

[Git](#git)

[Wie benutzt man Git?](#wie-benutzt-man-git)

[Github](#github)

[Markdown](#markdown)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Überschriften](#überschriften)
   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Fett, kursiv, durchgestrichen](#fett-kursiv-durchgestrichen)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Numerierungen](#numerierungen)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Tabellen](#tabellen)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Code](#code)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Horizontale Linien](#horizontale-linien)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Hyperlinks](#hyperlinks)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Bilder](#bilder)
   
   

---------
## Versionsverwaltungssysteme

Ein System zur Versionsverwaltung ist eine Software, die erfasst wann, wie und durch was sich Dateien verändert haben. Man kann jede Version jeder Datei jederzeit aufrufen und sehen, wer, wann, was verändert hat. 
Dieses Konzept ist in den letzten Jahren vor allem in der Softwareentwicklung zum Standard geworden. 

---------
## Git 
[Git](https://de.wikipedia.org/wiki/Git), entwickelt von Linus Torwalds, ist ein open-source Versionsverwaltungssystem, das sich in den letzen Jahren stark durchgesetzt hat. Mit Git hat man die Möglichkeit, all seine Projekte auf einem Server zu verwalten. Man kann sich entweder einen privaten Benutzer erstellen oder eine Organisation mit beliebig vielen Teilnehmern gründen. In einer solchen Organisation kann man bestimmen wer, welche Rechte auf welche Datei hat. Die Hierachie sieht folgendermaßen aus: Jeder Benutzer / jede Organisation kann ein neues **Repository** erstellen. Dies ist der Platz an dem alle Dateien eines Projektes sind. In jedem dieser Repositories gibt es mindestens einen **Branch** - den "master-Branch", auf dem vorerst alle Dateien gespeichert werden. Man kann aber auch kleinere Nebenprojekte in neuenn Branches speichern wenn man will. Man kann es auch mit Funktionen in C vergleichen: Der master-Branch ist die main-Funktion und jeder weiter Branch ist eine weiter Funktion. Funktionell sind alle Funktionen fast ident, aber die main-Funktion ist der Ausgangspunkt and dem alle anderen Funktionen starten. Wenn das Nebenprojekt in einem Branch fertig ist, kann es wieder in den master-Branch geführt werden, das heißt alle Änderungen sind jetzt im master-Branch. Man spricht auch von **merging**. Ab einem Branch geht die Hierachie wie in einer allbekannten Ordnerstruktur weiter. Man kann Dateien und Ordner, in denen man wieder Dateien anlegt, anlegen. Es gibt jedoch 3 Dateien, die an der Spitze eines Branches automatisch erstellt werden.
1. **.gitignore** - In dieser Datei wird festgelegt, welche Dateien in einem Repository von git erfasst und verwaltet werden sollen
2. **Licence** - Hier wird festgelegt welche Lizenz für dein Projekt gilt. Hat man keine Lizenz kann man oft leicht in rechtliche Schwierigkeiten kommen
3. **README.md** - In dieser Markdown-Datei kann der Besitzer Informationen über sein Projekt preisgeben

Eine Besonderheit von Git ist, dass jeder lokal eine gesamte Kopie des Repositories besitzt um auch offline arbeiten zu können. Man kann jederzeit beliebige Dateien mit dem Server synchronisieren.

### Wie benutzt man Git?
Git ist ein Programm ohne GUI, heißt es muss alles von einem Terminal aus geschehen. Um ein neues Repository anzulegen muss man sein Arbeitsverzeichnis auf den Ordner ändern, in dem man später sein lokes Repository haben möchte. Mit dem Befehl `git init` wird ein leeres Repository initaialisiert und ein `.git`-Ordner erstellt, in dem für Git relevante Dateien gespeichert sind. Falls man bereits ein Repository auf einem Server hat, das man auf einen Rechner herunterladen möchte kann man in einem gewünschten Arbeitsverzeichnis den Befehl `git clone <Link-zum-Repository>` ausführen. Nachem man sein lokales Repository erstellt hat kann man darin alle Dateien ansehen, bearbeiten, löschen oder neue Datien erstellen. Mit `git checkout <Branch>` kann man zu einem beliebigen Branch wechseln. Sobald eine Änderung des Repositories gemacht wird ist diese aber nicht autommatisch im Repository. Mit dem Befehl `git add <Dateiname>` wird eine Datei auf die "Warteliste" gesetzt um ins lokale Repository geladen zu werden. Mit dem Befehl `git commit -m "Kommentar zur Änderung"` werden alle Änderungen auf der Warteliste ins lokale Repository übernommen. Nun fehlt nur noch `git push` um das lokale Repository mit dem, auf dem Server zu synchronisieren. Falls sich das Repository auf dem Server in der Zwischenzeit geändert hat wird ein Algorithmus verwendet um zu entscheiden welche Änderungen übernommen werden. Zum Hochladen werden Benutzername und Passwort abgefragt. Vor dem erstmaligen ausführen von `git push` muss die email und der Name einmalig bekannt gegeben werden. Dies geschieht mit den Befehlen `git config --global user.email "email@example.com"` und `git config --global user.name "Max Mustermann"`. Um das lokale Repository auf den neuesten Stand zu bringen kann man den Befehl `git pull` verwenden. Eine erweiterte Liste mit Git-Befehlen findet man mit `git help`.

---------
## Github
[GitHub](https://de.wikipedia.org/wiki/GitHub) ist eine Online-GUI für Git die einen Server für private Projekte bereitstellt. GitHub ist auch für die Popularität von Git verantwortlich. Bei der Anlegung eines Repositories hat man die Wahl zwischen einem kostenfreien, öfftnelichen und einem kostenpflichtigen privaten Repository. Dadurch, dass öffentliche Projekte nun für jeden zugänglichh sind führt GitHub auch Lizenzen ein. Mit ihnen legt man fest was man bei der Verwendung seiner Dateien gefolgen muss. Legt man keine Lizenz fest kann man schnell in rechtliche Schwierigkeiten kommen. Auch eine README.md Datei wird hier als Standard eingeführt, in der der Ersteller des Projektes alle nötigen Informationen preisgibt. GitHub unterstützt auch die dirrekte Anzeige von Markdown.

## Markdown
[Markdown](https://www.wikipedia.org/wiki/Markdown) ist eine Skriptsprache mit der man besonders schnell und effizient formatierten Text schreiben kann. Zuerst beginnt man mit einer `*.md` Datei. Diese besteht rein aus plain-text und kann daher mit jedem beliebigen Texteditor bearbeitet werden. Nachdem man seine `*.md` Datei fertiggestellt hat braucht man einen Markdown-Interpreter um den Text formatiert anzeigen zu lassen. Bei GitHub ist bereits ein integrierter Markdown-Interpreter vorhanden. 
#### Überschriften
Es gibt 6 verschieden große Überschriften, die von `# Sehr große Überschrift` bis `###### Sehr kleine Überschrift` gehen. Die Anzahl der Hashes am Beginn bestimmen die Größe. Zwischen den Hashes und dem Text muss ein Leerzeichen sein.
#### Fett, kursiv, durchgestrichen
`**Dieser Text wird fett angezeigt werden**`, `*Dieser Text wird kursiv angezeigt werden*` und `~Dieser Text wird durchgestrichen angezeigt werden~`. Dabei sind auch kombinationen wie `***Fett und kursiv***`, `~*kursiv und durchgestrichen*~` und `~**Fett und durchgestrichen**~` möglich. Dabei dürfen weder nach dem ersten, noch vor dem letzten Steuerzeichen Leerzeichen stehen.
#### Numerierungen
Für eine ungeordnete Liste schreibt man einfach jeden Listenpunkt in eine neue Zeile mit einem `*` und einem Leeerzeichen davor.
Beispiel:
```
* Punkt 1
* Punkt 2
* Punkt 3
```
Für eine geordnete Liste gilt das gleiche, nur, dass man statt dem `*` eine Zahl mit einem Punkt dahinter schreibt. Welche Zahl man verwendet ist egal, es wird sowieso neu nummeriert.
Bei 
```
1. Punkt 1
1. Punkt 2
1. Punkt 3
```
wird der erste Punkt `1.`, der zweite `2.` usw. sein. Jedoch legt die erste Zahl fest, von wo weg numeriert werden soll. Ist die erste Zahl also eine 5, wird von 5 weg nummeriert.
#### Tabellen
Eine Tabelle zu erstellen sieht folgendermaßen aus:
```
a11|a12|a13
-----------
a21|a22|a23
-----------
a31|a32|a33
```
Man benötigt zur Trennung mehrerer Zeilen theoretisch nur 3 Bindestriche Auf die Maße der Tabelle hat man jedoch keinen Einfluss.
#### Code
Um code in einem Satz zu schreiben verwendet man `` `Code` ``. Um Code auf mehrere Zeilen zu verteilen, verwendet man

    ```
    Codezeile 1
    Codezeile 2
    Codezeile 3
    ```

In diesem Format unterstützt Markdown auchh Syntax-Highlighting. Man muss nur die Sprache nach den ersten ``` stellen. Zum Beispiel:
    
    ```C
    C-Code
    ```

    ```Java
    Java-Code
    ```

    ```LaTex
    LaTex-Code
    ```

#### Horizontale Linien
Für eine Horizontale Linie braucht man mindestens 3 Bindestriche, umgeben von jeweils einer Leerzeile. Ist diese Leerzeile nicht vorhanden, interpretiert Markdown die direkt angrenzenden Paragraphen als Header 1.

#### Hyperlinks
Um einen anklickbaren Link zu generieren kann man `[Anzeigetext](https://www.link-zu-einer-Webquelle.com)` schreiben.

#### Bilder
Bilder implementiert man ähnlich wie Hyperlinks und zwar mit `![Alternativtext](https://www.irgendeine-seite.com/image.png)`


[Hier](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/marsim17/protokolle/beispielseite.md) befindet sich eine Beispieldatei, in der alle oben genannten Befehle visualisiert werden.


