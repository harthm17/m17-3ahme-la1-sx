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
  * Strg + l ... Löschen des Bildschirms
  * Strg + c ... Abbrechen eines Kommandos
  * Strg + z ... Pausieren eines Kommandos
  * Strg + d ... Shell beenden
  * Strg + Shift + c ... Kopieren 
  * Strg + Shift + v ... Einfügen 

## Kommandos
> In einem Linux-System stehen viele Kommandos zur Verfügung. Da Kommandos oftmals nur Skripte sind, lässt sich das System durch eigene Skripte leicht erweitern.<br>

Eigene Skripte können vorzugsweise im Verzeichnis ~/bin abgelegt werden (das Verzeichnis muss eventuell erst angelegt werden). Beim Hochlauf wird geprüft, ob das Verzeichnis ~/bin vorhanden ist. Falls es existiert, wird es automatisch in die Umgebungsvariable PATH eingefügt.<br>

Natürlich können auch übersetzte C oder C++ Programme bzw. in anderen Programmier- oder Skriptsprachen wie Perl oder Phyton erstellte Programme anstelle von Skripts verwendet werden.<br>

Quelle: [LMS][lms] (Stand: 12.11.2019)

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

## Berechtigungen

> Grundlegende Dateirechte
Die grundlegenden Dateirechte lauten lesen (engl. read, kurz r), schreiben (engl. write, kurz w) und ausführen (engl. execute, kurz x):<br>
Lesen (r)<br>
Der Benutzer darf die Inhalte einer Datei auslesen bzw. im Falle eines Verzeichnisses dessen Inhalt auflisten.<br>
Schreiben (w)<br>
Der Benutzer darf in eine Datei schreiben bzw. im Falle eines Verzeichnisses Dateien und Unterverzeichnisse in diesem Verzeichnis erstellen, umbenennen und löschen sowie  deren Dateirechte ändern.<br>
Ausführen (x)<br>
Der Benutzer darf die Datei ausführen (als Programm) bzw. im Falle eines Verzeichnisses in dieses Verzeichnis wechseln und dort Dateien oder Unterverzeichnisse erreichen. Eine Datei oder ein Verzeichnis kann nur erreicht werden, wenn für alle übergeordneten Verzeichnisse ebenfalls das Ausführen-Recht vergeben wurde. Ohne das Lesen-Recht kann der Verzeichnisinhalt jedoch nicht aufgelistet werden.<br>

Quelle: [Variomedia][variomedia] (Stand: 12.11.2019)

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






[variomedia]: https://www.variomedia.de/faq/Wie-funktionieren-die-Datei--und-Verzeichnisrechte-auf-den-Webservern/article/290
[Wikipedia-Shell]: https://de.wikipedia.org/wiki/Bash_(Shell)
[lms]: https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/7BF1B31508DF3.symlink?resource_id=0-385942208&m=view#154334970
[Wikipedia-GitHub]: https://de.wikipedia.org/wiki/GitHub
[Git-gitignore]: https://git-scm.com/docs/gitignore
[Markdown-Formatierung]: https://support.zendesk.com/hc/de/articles/203691016-Formatieren-von-Text-mit-Markdown
