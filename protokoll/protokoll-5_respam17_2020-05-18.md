# Protokoll 5 Labor-SX 2020
--------------------------------
## Erstellung eines Daemon
* **Datum:** 18.05.2020
* **Fehlend:** --
* **Erstellt von:** Resch Paul
* **Übungsort:** Wegen Corona im Home-Office
---------------------------------
### Inhaltsangabe
* [tar.gz Datei](#targz-datei)
    * [Kommandos](#kommandos)
    * [Optionen](#optionen)
* [Fertigstellen des Arbeitsaufrags vom 11.5.](#fertigstellen-des-arbeitsaufrags-vom-115)
    * [Daemon](#erstellen-eines-daemon)
    * [Optionen bei den Kommandos](#3-optionen-bei-den-kommandos)
    * [Service-Datei](#4-service-datei)
    * [Automatischer Start](#5-automatischer-start)
* [Teilaufgabe 3](#teilaufgabe-3)

-------------------------------------
##### Teilaufgabe 1
### tar.gz Datei
Mit der Erklärung von SX und dem Praktischen Beispiel am Rechner von Herrn Pust, lernten wir die korrekte erstellung einer *tar.gz Datei* in der Shell. *tar* ist ein Programm um Dateien zu archivieren. Eine Archivdatei mit der Endung *tar.gz* ist zusätzlich noch komprimiert. Mehr Informationen dazu finden sie unter [https://wiki.ubuntuusers.de/tar/](https://wiki.ubuntuusers.de/tar/).

#### Kommandos
Mit folgenden Kommandos lässt sich eine Archivdatei in der Shell erstellen.

Das allgemeine Kommando lautet: *tar OPTIONEN Dateien*

In unserem Fall:
* tar -czf /tmp/archive1.tar.gz /root/.bash_history /home/paul4/.bash_history /home/paul4/mydaemon
* tar -tzf /tmp/archive1.tar.gz

#### Optionen
Hier lauten die Optionen zB. *-czf* oder *-tzf*. Was diese Verschiedenen Buchstaben bedeuten finden sie im oben angegebenen Link oder [hier](https://wiki.ubuntuusers.de/tar/).

------------------------------------------
##### Teilaufagbe 2
### Fertigstellen des Arbeitsaufrags vom 11.5.
###### 1.
Alles durchgelesen und verstanden.

###### 2.
### Erstellen eines Daemon
#### 1. 
Ein sogenannter Daemon (Dienst) ist ein Programm welches im Hintergrund abläuft. Es bedeutet so viel wie ***d**isk **a**nd **e**xecution **mon**itor*. So heißt es aber nur in einem Unixsystem. Unter Windosw wird ein solches Programm *services* oder *Systemdienste* genannt. Mehr Informationen zu einem Daemon auf [Wikipedia](https://de.wikipedia.org/wiki/Daemon).

#### 2. 
Aufgabe so wie im Buch beschrieben durchgeführt.

#### 3. Optionen bei den Kommandos
* **journalctl**:   *Abfrage der systemd journal*
> Query the systemd journal
* **journalctl -f**: --follow  *Zeigt die aktuellsten Einträge an*
> Show only the most recent journal entries, and continuously print new entries as they are appended to the journal.

* **journalctl -f -p 4**: --priority  *Zeigt Einträge mit einer Bestimmten Priorität an*
> Filter output by message priorities or priority ranges. Takes either a single numeric or textual log level (i.e. between 0/"emerg" and 7/"debug"), or a range of numeric/text log levels in the form FROM..TO. The log levels are the usual syslog log levels as documented in syslog(3), i.e.  "emerg" (0), "alert" (1), "crit" (2), "err" (3), "warning" (4), "notice" (5),"info" (6), "debug" (7). If a single log level is specified, all messages with this log level or a lower (hence more important) log level are shown. If a range is specified, all messages within the range are shown, including both the start and the end value of the range. This will add "PRIORITY=" matches for the specified priorities.

* **journalctl -f -v verbose**:   verbose *Zeigt die strukturierten Eingabepunkte mit allen Feldern*
> shows the full-structured entry items with all fields.

* **tail**:   *Zeigt die letzten Files an*
> output the last part of files
* **tail -f /var/log/syslog**:  --follow[={name|descriptor}] *Zeigt angehängte Daten, wenn die Datei wächst*
> output appended data as the file grows; an absent option argument means 'descriptor'

#### 4. Service-Datei
* **ExecStart**: Der Befehl wird beim Start der Unit ausgeführt.
* **IgnoreSIGPIPE**: Benötigt ein boolschen Wert. falls es *wahr* ist, so wird es im laufenden Prozess ignoriert.
* **KillMode**: Legt fest, wie die Prozesse dieser Unit getötet(beendet) werden sollen.

#### 5. Automatischer Start
Wie im Buch beschrieben durchgeführt. Alles funktioniert.

--------------------
##### Teilaufgabe 3
Kapitel 3 und 3.1 durchgelesen.












