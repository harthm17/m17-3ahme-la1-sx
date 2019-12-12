# WORK IN PROGRESS

# Laborprotokoll 9.12.2019 Pfanner


* **Thema:** Versionsverwaltung, Dokumentation mit Markdown
* **Datum:** 9.12.2019
* **Gefehlt:** -
* **Erstellt von:** Pfanner Jan


## Inhaltsverzeichnis

1. [Versionsverwaltung](#Versionsverwaltung)


## Versionsverwaltung

### Was ist Versionsverwaltung und wofür brauche ich es?

Ein **Versionsverwaltungsprogramm**, auch VCS (Version Control System genannt, z.B. [Git](https://de.wikipedia.org/wiki/Git), dient dem Speichern **verschiedener Versionen** von Dateien aller Art. Diese Dateien werden in sogenannten **Repositories** gespeichert und sind auch nach dem Aktualisieren noch in allen ursprünglichen Formen abrufbar.

Das VCS **Git**, entwickelt von [Linus Torvalds](https://de.wikipedia.org/wiki/Linus_Torvalds) brachte erstmals **branches** und **dezentrale Speicherung** ins Spiel und wird bis heute verwendet. Der Name stammt von einer im Englischen gebräuchlichen Beleidigung.

Ein VCS bringt eine ganze Reihe an Vorteilen mit sich. Einerseits gehen frühere Versionen von Dateien nie mehr verloren, da sie nicht überschrieben werden. Andererseits sind diese auch sicher gespeichert und mit Internetzugang abrufbar. Teamwork profitiert von der Einfachheit der Datenweiterleitung.
Einzig die zum Erlernen und Meistern benötigte Dauer ist ein Wehrmutstropfen an dieser Art der Speicherung, kann jedoch keinesfalls die positiven Aspekte überwiegen.


### Was kann Git?

Um mit Git zu arbeiten, ist die Website [Github](https://github.com) sinnvoll, die einem die Benutzeroberfläche für Git bietet. Man kann auch ohne GUI arbeiten, falls man das möchte. In Git werden Dateien wie gehabt in Repositories gespeichert, jedoch nicht nur auf dem Server, sondern auch in einem offline verfügbaren **local repository**. 
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
