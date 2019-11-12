# Protokoll m17-3ahme-la1
* **Datum:** 11.11.2019
* **Erstellt von:** Niklas Fuchshofer
-----------------------------------------

# Linux-Shell
* Effizienteres Arbeiten durch Verrkettung der Befehle
* leicht dokumentierbar
* Fernwartung mit schlechtem Internet möglich

> Bash (für Bourne-again shell) ist eine freie Unix-Shell und Teil des GNU-Projekts. Sie ist heute auf vielen unixoiden Systemen die Standard-Shell. Der Name ist absichtlich mehrdeutig und bedeutet unter anderem „wiedergeborene (born again) Shell“, „wieder (eine) Bourne-Shell“ oder auch aus dem Englischen to bash (schlagen, kritisieren, schlecht machen) bzw. umgangssprachlich „Party/Fete“.

Quelle: [Wikipedia][Wikipedia-Shell] (Stand: 12.11.2019)

-------------------

## Inhaltsverzeichniss

1. [Features](#features)
1. [Kommandos](#kommandos)
1. [Ebenen und Kommands](#git-ebenen-und-kommands)
1. [Workflow](#git-workflow)
1. [.gitignore](#gitignore)
1. [Markdown](#markdown)

## Features
  * Autovervollständigung durch die Tabulatortaste<br>

**Hotkeys:** 
  * Strg + l ... Löschen des Bildschirms
  * Strg + c ... Abbrechen eines Kommandos
  * Strg + z ... Pausieren eines Kommandos
  * Strg + d ... Shell beenden
  * Strg + Shift + c ... Kopieren 
  * Strg + Shift + v ... Einfügen 

## Kommandos
> GitHub ist ein Onlinedienst, der Software-Entwicklungsprojekte auf seinen Servern bereitstellt (Filehosting).
Namensgebend war das Versionsverwaltungssystem Git. Die GitHub, Inc. hat ihren Sitz in San Francisco in den USA.
Ähnliche Dienste sind GitLab und Bitbucket.

Quelle: [Wikipedia][Wikipedia-GitHub] (Stand: 22.10.2019)

### Kommandos für Dateien und Verzeichnisse
Befehl | Bedeutung | Erklärung
-------- | -------- | --------
pwd |      print working directory |  Aktuelles Arbeitsverzeichnis (.) ausgeben<br>
ls |      list directory content | Dateien und Verzeichnisse von ./ ausgegeben
cd  |    change directory       |   In ein (anderes) Verzeichnis wechseln<br>
touch |    touch file        |        Leere Datei anlegen oder Zeitstempel ändern<br>
mkdir |   make directory     |       Verzeichnis erstellen<br>
mv    |   move              |        Datei/Verzeichnis verschieben oder umbenennen<br>
cp   |    copy           |           Date/Verzeichnis kopieren<br>
scp  |    secure copy     |          copy über Netzwerk via ssh (secure shell)<br>
rm   |    remove             |       Datei oder löschen<br>
rmdir |   remove directory     |     Verzeichnis löschen (muss leer sein!)<br>
ln   |    link               |       Links erstellen<br>
cat   |   concatenate        |       Dateien verbinden und auf stdout ausgeben<br>
less   |  less     |       Dateiinhalt im Viewer less anzeigen<br>
hexdump | hexadecimal file dump |    Dateiinhalt als Hexdump ausgeben<br>
grep   |  global search for a   |    Auf ein Suchmuster passende Zeilen ausgeben<br>
find |    find files           |     Dateien oder Verzeichnisse finden<br>
dd   |    duplicate data      |      Daten 1:1 kopieren (auch auf Geräte anwendbar) <br>
df   |    disk free space     |      Freien Speicher auf Dateisystemen anzeigen<br>
du   |    disk usage           |     Byte-Verbrauch in Verzeichnis(sen) zeigen<br>
mount  |  mount a filesystem    |    Partition einbinden<br>
umount  | unmount a filesystem   |   Eingebundene Partition trennen<br>

## Git-Ebenen und Kommands

Abbildung 1 ![](https://readsahil.files.wordpress.com/2016/09/git_cheat_sheet.png?w=636g)

-------------

* git status 
* git reset  
* git reset --hard 
* git commit -m *text* 
* git checkout *branch* 

## Git-Workflow

Abbildung 2 ![](https://arccwiki.uwyo.edu/images/1/19/GitHub_Flow_steps.png)

-------------

### Verwendeter Workflow

1. git clone *link*
2. git pull *name*
3. cd *name*
3. git checkout *branch*
3. (nano *dateiname*)
3. git add *dateiname*
3. git commit -m *text*
3. git push

## .gitignore
> A gitignore file specifies intentionally untracked files that Git should ignore. Files already tracked by Git are not affected.

Quelle: [Git][Git-gitignore] (Stand: 23.10.2019)

## Markdown
Endung: * .md
> Markdown ist eine vereinfachte Auszeichnungssprache, die von John Gruber und Aaron Swartz entworfen und im Dezember 2004 mit Version 1.0.1 spezifiziert wurde.
Ein Ziel von Markdown ist, dass schon die Ausgangsform ohne weitere Konvertierung leicht lesbar ist.
Als Auszeichnungselemente wurden daher vor allem Auszeichnungsarten verwendet, die in Plain text und E-Mails üblich sind.

Quelle: [Wikipedia][Wikipedia-Markdown] (Stand 22.10.2019)

[Markdown-Formatierung][Markdown-Formatierung]







[Wikipedia-Shell]: https://de.wikipedia.org/wiki/Bash_(Shell)
[Wikipedia-Markdown]: https://de.wikipedia.org/wiki/Markdown
[Wikipedia-GitHub]: https://de.wikipedia.org/wiki/GitHub
[Git-gitignore]: https://git-scm.com/docs/gitignore
[Markdown-Formatierung]: https://support.zendesk.com/hc/de/articles/203691016-Formatieren-von-Text-mit-Markdown
