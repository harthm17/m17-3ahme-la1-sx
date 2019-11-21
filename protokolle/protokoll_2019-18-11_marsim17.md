# Protokoll LA1/SX 3AHME (2019/20)

* **Thema:** Versionsverwaltungssysteme, Markdown, git, Github
* **Datum:** 18.11.2019
* **Gefehlt:** -
* **Erstellt von:** Marcher Simon
* **Protokoll nächste Einheit:** [Protokoll 25.11.2019](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/marsim17/protokolle/protokoll_2019-25-11_marsim17.md)
---------
## Inhaltsverzeichnis

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
Git ist ein Programm ohne GUI, heißt es muss alles von einem Terminal aus geschehen. Um ein neues Repository anzulegen muss man sein Arbeitsverzeichnis auf den Ordner ändern, in dem man später sein lokes Repository haben möchte. Mit dem Befehl `git init` wird ein leeres Repository initaialisiert und ein `.git`-Ordner erstellt, in dem für Git relevante Dateien gespeichert sind. Falls man bereits ein Repository auf einem Server hat, das man auf einen Rechner herunterladen möchte kann man in einem gewünschten Arbeitsverzeichnis den Befehl `git clone <Link-zum-Repository>` ausführen. Nachem man sein lokales Repository erstellt hat kann man darin alle Dateien ansehen, bearbeiten, löschen oder neue Datien erstellen. Mit `git checkout <Branch>` kann man zu einem beliebigen Branch wechseln. Sobald eine Änderung des Repositories gemacht wird ist diese aber nicht autommatisch im Repository. Mit dem Befehl `git add <Dateiname>` wird eine Datei auf die "Warteliste" gesetzt um ins lokale Repository geladen zu werden. Mit dem Befehl `git commit -m "Kommentar zur Änderung"` werden alle Änderungen auf der Warteliste ins lokale Repository übernommen. Nun fehlt nur noch `git push` um das lokale Repository mit dem, auf dem Server zu synchronisieren. Falls sich das Repository auf dem Server in der Zwischenzeit geändert hat wird ein Algorithmus verwendet um zu entscheiden welche Änderungen übernommen werden. Zum Synchronisieren werden Benutzername und Passwort abgefragt. Eine erweiterte Liste mit Git-Befehlen findet man mit `git help`.
---------
## Github
[GitHub](https://de.wikipedia.org/wiki/GitHub) ist eine Online-GUI für Git die einen Server für private Projekte bereitstellt. GitHub ist auch für die Popularität von Git verantwortlich. Bei der Anlegung eines Repositories hat man die Wahl zwischen einem kostenfreien, öfftnelichen und einem kostenpflichtigen privaten Repository. Dadurch, dass öffentliche Projekte nun für jeden zugänglichh sind führt GitHub auch Lizenzen ein. Mit ihnen legt man fest was man bei der Verwendung seiner Dateien gefolgen muss. Legt man keine Lizenz fest kann man schnell in rechtliche Schwierigkeiten kommen. Auch eine README.md Datei wird hier als Standard eingeführt, in der der Ersteller des Projektes alle nötigen Informationen preisgibt. GitHub unterstützt auch die dirrekte Anzeige von Markdown.

## Markdown
[Markdown](https://www.wikipedia.org/wiki/Markdown) ist eine Skriptsprache.

