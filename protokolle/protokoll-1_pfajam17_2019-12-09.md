# Laborprotokoll 9.12.2019 Pfanner


* **Thema:** Versionsverwaltung, Dokumentation mit Markdown
* **Datum:** 9.12.2019
* **Gefehlt:** -
* **Erstellt von:** Pfanner Jan


## Inhaltsverzeichnis

1. [Versionsverwaltung](#versionsverwaltung)
  * [Was ist Versionsverwaltung?](#was-ist-versionsverwaltung-und-wofür-brauche-ich-es)
  * [Was kann Git)](#was-kann-git)
  * [Anfänge mit Github](#wie-fange-ich-mit-github-an)
2. [Markdown](#markdown)
  * [Was ist Markdown?](#was-ist-markdown)
  * [Warum Markdown?](#warum-markdown)
  * [Formatierung in Markdown](#formatierungen-in-markdown)

## Versionsverwaltung

### Was ist Versionsverwaltung und wofür brauche ich es?

Ein **Versionsverwaltungsprogramm**, auch VCS (Version Control System genannt, z.B. [Git](https://de.wikipedia.org/wiki/Git), dient dem Speichern **verschiedener Versionen** von Dateien aller Art. Diese Dateien werden in sogenannten **Repositories** gespeichert und sind auch nach dem Aktualisieren noch in allen ursprünglichen Formen abrufbar.

Das VCS **Git**, entwickelt von [Linus Torvalds](https://de.wikipedia.org/wiki/Linus_Torvalds) brachte erstmals **branches** und **dezentrale Speicherung** ins Spiel und wird bis heute verwendet. Der Name stammt von einer im Englischen gebräuchlichen Beleidigung.

Ein VCS bringt eine ganze Reihe an Vorteilen mit sich. Einerseits gehen frühere Versionen von Dateien nie mehr verloren, da sie nicht überschrieben werden. Andererseits sind diese auch sicher gespeichert und mit Internetzugang abrufbar. Teamwork profitiert von der Einfachheit der Datenweiterleitung.
Einzig die zum Erlernen und Meistern benötigte Dauer ist ein Wehrmutstropfen an dieser Art der Speicherung, kann jedoch keinesfalls die positiven Aspekte überwiegen.


### Was kann Git?

Um mit Git zu arbeiten, ist die Website [GitHub](https://github.com) sinnvoll, die einem die Benutzeroberfläche für Git bietet. Man kann auch ohne GUI arbeiten, falls man das möchte. In Git werden Dateien wie gehabt in Repositories gespeichert, jedoch nicht nur auf dem Server, sondern auch in einem offline verfügbaren **local repository**. 
Git bietet die Möglichkeit an, in jedem Repository branches anzulegen. Der sogenannte **Master Branch** ist hierbei die Hauptstraße des Repositories und beherbergt in der Regel die stabile Version der Dateien. Sollte man Änderungen vornehmen wollen, ohne Schaden anzurichten, bietet sich das Erstellen eines **Side Branches** an. In diesem werden alle Dateien des Master Branches kopiert und können unabhängig von diesem bearbeitet werden. Ist die Arbeit komplett, kann man mit einer **pull request** das Eingliedern des Side Branches in den Master Branch erbitten. Als letzter Schritt erfolgt der **merge**, die Verschmelzung der Branches.

Folgende Befehle werden in der Linux-Konsole zum Arbeiten mit Git benötigt:

* git clone *repository-link*

Mit *git clone* wird das online verfügbare repository auf den lokalen Rechner kopiert. Dies ist die Grundlage für Arbeiten mit Git.

* git status

Mit git status erfährt man beispielsweise, in welchem branch man sich gegenwärtig befindet.

* git checkout *Branch-name*

Hiermit wird in den angegebenen branch gewechselt.

* git add *Dateiname*

Mit diesem Befehl wird eine Datei in den sogenannten **Index** geschoben. Hier ist sie gewissermaßen in der Warteschlange, jedoch noch nicht im local repository.

* git commit -m "Kommentar"

Dieser Befehl schiebt alle Dateien vom Index in das local repository. Gegebenenfalls muss man bei erstmaliger Benutzung eine Konfiguration mit Name und E-Mail-Adresse durchführen. Diese werden nicht überprüft.

* git push 

Git push übermittelt nun das local repository an den Server, wo es als remote repository gespeichert wird und abrufbereit ist. Nutzername und Passwort müssen beim Ausführen des Befehls eingegeben werden.

## Wie fange ich mit GitHub an?

Um mit GitHub zu arbeiten, muss man sich erst registrieren. Dies geht einfach auf der [Hauptseite](https://github.com/), mit Accountverifizierung per E-Mail. 
Hat man dies geschafft, geht es ans Erstellen des ersten Repositories. Dazu sucht man den **Repositories**-Reiter im Nutzerprofil auf und drückt die grüne **New**-Taste. Nach Benennen des Repositories bietet sich einem die Möglichkeit, mihthilfe einer **Gitignore**-Vorlage die Art des Repositories anzupassen. Dabei sind zahlreiche Optionen verfügbar, für diverse Programmiersprachen und andere Projekttypen. Neben dem Gitignore hat man auch die Möglichkeit, vorgefertigte **Lizenzvereinbarungen** über den Inhalt des Reporitories gültig zu machen. Ohne Lizenz ist alles im Repository rechtlich ungeschützt. Dies gilt es zu vermeiden.

**Besondere Vorsicht:** Falls man die Gratisversion von Github verwendet, sollte man keinesfalls ein **Private Repository** erstellen. Dieses Feature gibt es nur in der kostenpflichtigen Version. Durch Auswählen beginnt automatisch eine befristete Probezeit.

Die letzte Funktion der Repository-Erstellungsseite, das Initialisieren des Repositories mit einer **README-Datei**, ist empfehlenswert. Die README ist beim Öffnen des Repositories im Browser als erstes sichtbar und sollte daher die Navigation des Repositories unterstützen. Wenn man ein vorhandenes Repository kopiert, kann dieser Schritt ausgelassen werden.

Hat man alle Parameter entsprechend gesetzt, bleibt bloß noch die grüne Taste am Seitenfuß, **Create repository**. Glückwunsch!

## Markdown

### Was ist Markdown?

[Markdown](https://de.wikipedia.org/wiki/Markdown) ist eine Skriptsprache, die einfache Dokumentierung ermöglicht. Sie wird z.B. auf Github verwendet.
Markdown speichert eingegebenen Text als Plain Text.

### Warum Markdown?

Im Vergleich zu anderen Dokumentationsmethoden ist Markdown sowohl praktisch als auch umfangreich. Lesbarer und verwertbarer als handschriftliche Dokumentation, speicherfreundlicher als Bilder, schneller als bloße Textverarbeitung. 

### Formatierungen in Markdown

Eine schnelle Einführung in die verschiedenen Formatierungsmöglichkeiten, die Markdown bietet, findet sich [hier](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet), eine umfangreichere Erklärung speziell für *Markdown Here* [hier](https://github.com/adam-p/markdown-here/wiki/Markdown-Here-Cheatsheet)
