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

## Git 
![Git-Logo](https://de.wikipedia.org/wiki/Git#/media/Datei:Git-logo.svg)
[Git](https://de.wikipedia.org/wiki/Git), entwickelt von Linus Torwalds, ist ein open-source Versionsverwaltungssystem, das sich in den letzen Jahren stark durchgesetzt hat. Mit Git hat man die möglichkeit, all seine Projekte auf einem Server zu verwalten. Man kann sich entweder einen privaten Benutzer erstellen oder eine Organisation mit beliebig vielen Teilnehmern gründen. In einer solchen Organisation kann man bestimmen wer, welche Rechte auf welche Datei hat. Die Hierachie sieht folgendermaßen aus: Jeder Benutzer / jede Organisation kann ein neues **Repository** erstellen. Dies ist der Platz an dem alle Dateien eines Projektes sind. In jedem dieser Repositories gibt es mindestens einen **Branch** - den "master-Branch", auf dem vorerst alle Dateien gespeichert werden. Man kann aber auch kleinere Nebenprojekte in neuenn Branches speichern wenn man will. Man kann es auch mit Funktionen in C vergleichen: Der master-Branch ist die main-Funktion und jeder weiter Branch ist eine weiter Funktion. Funktionell sind alle Funktionen fast ident, aber die main-Funktion ist der Ausgangspunkt and dem alle anderen Funktionen starten. Wenn das Nebenprojekt in einem Branch fertig ist, kann es wieder in den master-Branch geführt werden, das heißt alle Änderungen sind jetzt im master-Branch. Man spricht auch von **merging**. Ab einem Branch geht die Hierachie wie in einer allbekannten Ordnerstruktur weiter. Man kann Dateien und Ordner, in denen man wieder Dateien anlegt, anlegen. Es gibt jedoch 3 Dateien, die an der Spitze eines Branches automatisch erstellt werden.
1. .gitignore
	In dieser Datei wird festgelegt, welche Dateien in einem Repository von git erfasst und verwaltet werden sollen
2. Licence 
	Hier wird festgelegt welche Lizenz für dein Projekt gilt. Hat man keine Lizenz kann man oft leicht in rechtliche Schwierigkeiten kommen
3. README.md
	In dieser Markdown-Datei kann der Besitzer Informationen über sein Projekt preisgeben

## Github
[GitHub](https://de.wikipedia.org/wiki/GitHub) ist ein kostenfreier Onlinedienst der 

### Die Funktionsweise
Jeder mit einem email-Account kann sich ein GitHub Profil anlegen. Mit diesem Profil kann man sogenannte Repositories anlegen
