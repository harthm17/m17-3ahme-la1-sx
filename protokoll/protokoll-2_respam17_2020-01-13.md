# Protokoll 2 Labor-SX 2019/20
---------------------------------
* **Thema:** Linux Grundlagen (Konsole/Komandos)
* **Datum:** 13.01.2020
* **Fehlend:** *Jan Pfanner*
* **Erstellt von:** Paul Resch
---------------------------------
## Inhaltsverzeichnis
1. [Konsole](#konsole)
      * [Vorteile](#vorteile)
      * [Nachteile](#nachteile)
1. [Grundlegendes und Tastenkombinationen](#grundlegendes-und-tastenkombinationen)
1. [Kommandos](#kommandos)
      * [Für Dateien und Verzeichnisse](#für-dateien-und-verzeichnisse)
      * [Für Betriebssystem und Prozesse](#für-betriebssystem-und-prozesse)
      * [Für die Benutzerverwaltung](#für-die-benutzerverwaltung)
      * [Systemkommandos](#systemkommandos)
      * [Terminalkommandos](#terminalkommandos)
      * [Editoren](#editoren)
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
*Strg L* | | löscht den Bildschirm (mit dem Kommando *reset* wird die Shell zurückgesetzt)
*Strg C* | | Kommando abbrechen
*Strg Z* | | Kommando pausieren
*Strg +* | | Schriftgröße verändern -> vergrößern
*Strg -* | | Schriftgröße verändern -> verkleinern
*Strg Shift C* | | kopieren
*Strg Shift V* | | einfügen
_ | *Enter* | Kommandos werden mit der *Entertaste* abgeschlossen und somit anschließend ausgeführt
_ | *Tabulator* | Autovervollständigung
_ | *Pfeiltaste* ⇧⇩ | History (fühere Kommandos auswählen)
_ | *Pfeiltaste* ⇦⇨ | Cursor bewegen

* Mit dem **&** am Ende eines Kommandos wird dies im **Hintergrund ausgeführt**
* Mit dem **Pipe Operator |** kann man Kommandos **verketten**
* Mit dem **;** als Trennzeichen kann man **mehrere Kommandos** in einer Zeile verwenden
--------------------------------------------

### Kommandos

Kommandos aus [Skript (8 Grundlegende Kommandos)](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/7BF1B31508DF3.symlink?resource_id=0-385942208&m=view#154334970) sowie [Skript (14 Weitere Kommandos)](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/7BF1B31508DF3.symlink?resource_id=0-385942208&m=view#155382209)

#### Für Dateien und Verzeichnisse
Kommando | Bedeutung | Beschreibung
------- | ---- | ------------
pwd | print working directory | Aktuelles Arbeitsverzeichnis (.) ausgeben
**ls** | list directory content | Dateien und Verzeichnisse von ./ ausgegeben
ls /etc/apt | | Dateien und Verzeichnisse von /etc/apt ausgeben
ls -l | | Line-Mode, mehr Infos anzeigen
ls -a | | all, auch verborgene Dateien anzeigen
**cd** | change directory | In ein (anderes) Verzeichnis wechseln
cd /etc/apt | | in das verzeichnis /etc/apt wechseln
cd .. | | in das übergeordnete Verzeichnis wechseln
mkdir | make directory | Verzeichnis erstellen
rmdir | remove directory | Verzeichnis löschen (muss leer sein!)
mv | move | Datei/Verzeichnis verschieben oder umbenennen
cp | copy | Datei/Verzeichnis kopieren
rm | remove | Datei löschen
rm -r | | Datei oder Verzeichnis samt Inhalt löschen
cat |  concatenate | Dateien verbinden und auf stdout ausgeben
less | less (is more) | Dateiinhalt im Viewer less anzeigen
hexdump | hexadecimal file dump | Dateiinhalt als Hexdump ausgeben
find | find files | Dateien oder Verzeichnisse finden

#### Für Betriebssystem und Prozesse
Kommando | Bedeutung | Beschreibung
------- | ---- | ------------
date | print system date and time | Aktuelle Zeit ausgeben
jobs | show user processes | Eigene Prozesse anzeigen
kill | kill/signal process | Signal an Prozess senden, Prozess beenden

#### Für die Benutzerverwaltung
Kommando | Bedeutung | Beschreibung
------- | ---- | ------------
whoami | who am i | aktuellen Benutzer ausgeben
who | who is logged on | wer ist gerade angemeldet
passwd | set new password | Passwort neu setzen
sudo | super-user do | in den Super-User Mode (root) wechseln
groups | display groups | Gruppenmitgliedschaft anzeigen
adduser | add new user | Neuen Benutzer hinzufügen
deluser | delete user | Benutzer entfernen

#### Systemkommandos
Kommando | Bedeutung | Beschreibung
------- | ---- | ------------
exit | exit from current process | Beende aktuelles Programm (bash, screen, ...)
login | log in in new shell | Neue Login-Shell (bash) starten
logout | log out from shell | Aus aktueller Login-Shell abmelden
poweroff | power off the system | System abschalten
reboot | reboot the system | System neu starten

#### Terminalkommandos
Kommando | Bedeutung | Beschreibung
------- | ---- | ------------
reset | reset terminal | Terminal in den Grundzustand zurücksetzen
clear | clear screen | Terminalschirm leeren (scroll nach unten)
echo | echo text | Text oder Variable auf stdout (Terminal) ausgaben

#### Editoren
Kommando/Name | Beschreibung
------------- | ------------
nano | Terminalbasierender Editor
vi | Standard-Editor für Linux (Modal-Editor)
emacs | Mächtiger Editor für Programmierer
