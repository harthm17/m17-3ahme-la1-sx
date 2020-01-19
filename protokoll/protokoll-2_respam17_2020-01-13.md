# Protokoll 2 Labor-SX 2019/20
---------------------------------
* **Thema:** Linux Grundlagen (Konsole/Komandos)
* **Datum:** 13.01.2020
* **Fehlend:** Jan Pfanner
* **Erstellt von:** Paul Resch
---------------------------------
## Inhaltsverzeichnis
1. [Konsole](#konsole)
    * [Shell](#unix-shell)
    * [Vorteile](#vorteile)
    * [Nachteile](#nachteile)
2. [Grundlegendes und Tastenkombinationen](#grundlegendes-und-tastenkombinationen)
---------------------------------
### Konsole
Die Konsole bzw. die Shell ist ein Program zur Komunikation mit dem Betriebssystem.

Unix-Shell laut [Wikipedia](https://de.wikipedia.org/wiki/Unix-Shell):
> Die Unix-Shell oder kurz Shell (englisch für Hülle, Schale) bezeichnet die traditionelle Benutzerschnittstelle unter Unix oder unixoiden Computer-Betriebssystemen.

Verwendet wird die **Bourne-again shell** ([Bash](https://de.wikipedia.org/wiki/Bash_(Shell)))
> Bash (auch BASH oder bash), die Bourne-again shell, ist eine freie Unix-Shell unter GPL. 
Als Shell ist Bash eine Mensch-Maschine-Schnittstelle, die eine Umgebung (englisch environment) bereitstellt, in der zeilenweise Texteingaben und -ausgaben möglich sind. Letzteres erfolgt über die Befehlszeile, in die Befehle eingetippt und durch betätigen der Eingabetaste eingegeben werden.

#### Vorteile
* Effizientes Arbeiten
* Auch bei schlechter Netzwerkverbuindung verwendbar
* Auch ohne Grafische Benutzeroberfläche verwendbar

#### Nachteile
* Man muss sich intensiv damit beschäftigen

-------------------------------------------------

### Grundlegendes und Tastenkombinationen
Tastenkombination | Taste | Beschreibung 
----------------- |------ | ------------
*Strg Alt T* | | öffnet die Konsole (bei Linux)
*Strg D* | | Shell beenden
*Strg L* | | löscht den Bildschirm (mit dem Komando *reset* wird die Shell zurückgesetzt)
*Strg C* | | Komando abbrechen
*Strg Z* | | Komando pausieren
*Strg +* | | Schriftgröße verändern -> vergrößern
*Strg -* | | Schriftgröße verändern -> verkleinern
*Strg Shift C* | | kopieren
*Strg Shift V* | | einfügen
_ | *Enter* | Komandos werden mit der *Entertaste* abgeschlossen und somit anschließend ausgeführt
_ | *Tabulator* | Autovervollständigung
_ | *Pfeiltaste* ⇧⇩ | History (fühere Komandos auswählen)
_ | *Pfeiltaste* ⇦⇨ | Cursor bewegen

* Mit dem **&** am Ende eines Komandos wird dies im **Hintergrund ausgeführt**
* Mit dem **Pipe Operator |** kann man Komandos **verketten**
* Mit dem **;** als Trennzeichen kann man **mehrere Komandos** in einer Zeile verwenden
--------------------------------------------

### Komandos

