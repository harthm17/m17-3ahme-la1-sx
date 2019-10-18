# Protokoll LA1 / 3AHME (2019/20)
* **Thema:** Linux / Shell
* **Datum:** 14.10.2019
* **Gefehlt:** ---
* **Erstellt von:** strrim17
* **Protokoll letzte Einheit:** [Git / Github (Markdown)](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/edit/strrim17/strrim17/protokolle/protokoll_2019-09-30_strrim17.md)

------------------------------------------------------------------------------------------------------------------------

## Inhaltsverzeichnis

1. [Linux](#linux)
   1. [Partitionen](#partitionen)
   2. [Dateien](#dateien)
   3. [Verzeichnisse](#verzeichnisse)
2. [Shell](#shell)
   1. [SSH](#ssh)
   2. [Ein -und Ausloggen](#ein--und-ausloggen)
      1. [Mount](#mount)
      2. [Unmount](#unmount)
   3. [Unix-Dateirechte](#unix-dateirechte)
      1. [Benutzerklassen](#benutzerklassen)
      2. [Grundlegende Rechte](#grundlegende-rechte)
      3. [Symbolische Notation](#symbolische-notation)
3. [Links](#links)

------------------------------------------------------------------------------------------------------------------------

## Linux
Als Linux oder GNU/Linux bezeichnet man in der Regel freie, unixähnliche Mehrbenutzer-Betriebssysteme, die auf dem Linux-Kernel und wesentlich auf GNU-Software basieren.

### Partitionen
Mithilfe der Partition können Datenträger in mehrere Teile, sogenannte Partitionen aufgeteilt werden. Diese Partitionen werden von Linux als Block-Device im Verzeichnis /dev zur Verfügung gestellt.

Beispiel:

```
schueler@pcxx:~$ ls /dev
autofs           loop3                  stderr   tty34   tty63       ttyS5
block            loop4                  stdin    tty35   tty7        ttyS6
bsg              loop5                  stdout   tty36   tty8        ttyS7
btrfs-control    loop6                  tty      tty37   tty9        ttyS8
bus              loop7                  tty0     tty38   ttyprintk   ttyS9
cdrom            loop-control           tty1     tty39   ttyS0       uhid
.
.
.
```

**Partition** steht für:
* die Landesteilung in der Politik
* in der Mengenlehre eine Unterteilung von Mengen
* in der Zahlentheorie die Partitionsfunktion
* in der Graphentheorie eine spezielle Zerlegung der Knotenmenge eines Graphen
* die Unterteilung von Datenträgern
* ein Member (Partition) des Dateisystems (Library) auf IBM-Großrechnern

**Partitionierung (auch Partitionieren genannt)** steht für:
* allgemein für den Vorgang eines Aufteilens; eine Partitionierung kann auch das entstandene System aus Partitionen meinen.
* ein Entscheidungsproblem aus der theoretischen Informatik unter Anwendung der mathematischen Zahlentheorie
* die Aufteilung einer Schaltung in Teilschaltungen (Partitionen) beim Layout- bzw. Chipentwurf
* die Aufteilung eines Servers zur gleichzeitigen Nutzung durch mehrere Betriebssysteminstanzen
* bei Datenbanken die Aufteilung einer Tabelle in mehrere Teile
* die Trennung radioaktiven Abfalls in verschiedene Bestandteile

Quelle: [https://de.wikipedia.org/wiki/Partition]

### Dateien
Eine Datei beinhaltet Informationen und ist technisch betrachtet eine Ansammlung von Bytes die auf einem Datenträger gespeichert sind.

#### Arten von Dateien
Nach ihrem Inhalt unterscheidet man unter anderem:
* ausführbare Dateien 
* Programme in Maschinensprache
* Programme in Skriptsprachen
* Programme in einem Zwischencode (Bytecode)
* nichtausführbare Dateien 
* Programme im Quelltext
* Textdateien
* Audiodateien, zum Beispiel WAV, MIDI, MP3
* Bilddateien
* Datenbankdateien
* Dateiverknüpfung
* allgemein: Binärdateien (z. B. von proprietären Programmen zur Datenspeicherung verwendet)
* …

Quelle: [https://de.wikipedia.org/wiki/Datei]

### Verzeichnisse
Verzeichnisse sind eigentlich auch Dateien, spezielle Dateien. In Verzeichnissen können andere Dateien (und somit auch weitere Verzeichnisse) abgelegt werden. Über Verzeichnisse kann daher ein Dateiname und damit eine Datei (also eine bestimmte Information) vom System gefunden werden. Es bildet sich dadurch eine baumartige Struktur, ein Verzeichnisbaum.

Beispiele der angegebenen Verzeichnisse:

```
schueler@pcxx:~$ ls
Desktop     examples.desktop   pidgin      Videos
Documents   Music              Public      Templates
Downloads   Pictures
```

------------------------------------------------------------------------------------------------------------------------

## Shell
Sowohl Windows als auch Linux verfügen über eine Shell (Eingabekonsole), über die das System mit textuellen Kommandos gesteuert bzw. konfiguriert werden kann. Bei Linux ist diese Konsole sehr mächtig und sehr effizient anwendbar.

**Vorteile:**
Effizienteres Arbeiten nach Einarbeitung
Die Befehle und Befehlsketten sind leicht dokumentierbar.
Eine Verkettung von Befehlen ermöglicht die effiziente Lösung einer Aufgabe.
Auch bei Fernwartung über schlechte Netzwerkverbindung verwendbar.
Auch auf Systemen ohne GUI-Desktop verwendbar (zB Embedded Systemen)

**Nachteile:**
Keine intuitive Arbeitsweise
Erfordert eine gründliche Schulung.
Nur für Experten oder den interessierten Power-User geeignet.

### SSH
Der Begriff "SSH" bezeichnet einerseits ein Netzwerkprotokoll und andererseits das dazu passende Programm. Mit der Secure Shell SSH ist es möglich eine sichere (verschlüsselte) Verbindung zwischen zwei Rechnern aufzubauen. SSH ersetzt das Vorgängersystem Telnet.

### Ein -und Ausloggen
Verschiedene Geräte werden mit den Befehlen ```mount``` und ```unmount``` ein- bzw. ausgehängt.

#### Mount
Mounten bzw. Einhängen, Einbinden oder Aktivieren, bezeichnet bei Unix sowie einigen anderen Betriebssystemen den Vorgang, ein Dateisystem an einer bestimmten Stelle – dem Einhängepunkt – verfügbar zu machen, damit der Benutzer auf die Dateien zugreifen kann.

#### Unmount
Das Gegenteil von Mounten ist Unmounten, Dismounten oder Aushängen. Dazu ist es erforderlich, dass kein Prozess mehr auf Dateien auf dem Dateisystem zugreift und dass alle Daten auf das Dateisystem geschrieben sind. Das Betriebssystem versucht daher, alle jene Prozesse geordnet zu beenden, die noch offene bzw. unvollendete Zugriffe aufweisen – kann dies nicht erreicht werden, so schlägt das Aushängen fehl. Kann ein Programm oder Prozess diese Ressourcen nicht freigeben, weil sie zur Ausführung notwendig sind, lässt sich ein Dateisystem daher nicht aushängen: ein prominentes Beispiel dafür ist das Systemlaufwerk (englisch Boot Volume) eines Betriebssystems. 
Wird ein Dateisystem ohne Unmounten entfernt (z. B. ein USB-Stick abgezogen), kann es unter Umständen zu Datenverlust oder Zerstörung der Datenintegrität auf dem Dateisystem kommen, wenn noch nicht alle Daten auf das Dateisystem geschrieben wurden.

Quelle: [https://de.wikipedia.org/wiki/Mounten]

### Unix-Dateirechte
Die Unix-Dateirechte sind Dateiberechtigungen bei Unix und Unix-Derivaten wie Linux und Mac OS X. Die Berechtigungsaufteilung in Eigentümer, Gruppe und Andere gibt es seit UNIX-V4 (1974). Die aktuellen UNIX-Dateirechte zeichnen sich durch eine einfache Struktur aus, die einerseits intuitiv von Menschen verwendet werden kann und andererseits keine hohen Ansprüche an Computer stellt.

#### Benutzerklassen
Auf Unix-Dateisystemen besitzt jeder Inode, d. h. im Endeffekt jede Datei, eine Regelung der Zugriffsrechte. Geregelt werden die Rechte folgender Benutzerklassen:

**Eigentümer**
ein spezielles Benutzerkonto am Computer
**Gruppe**
eine spezielle Unix-Benutzergruppe
**Sonstige**
jeder andere, der nicht der Eigentümer oder ein Mitglied der Inhabergruppe ist.

#### Grundlegende Rechte
Jede der drei Benutzerklassen kann eines oder mehrere der folgenden Rechte zugewiesen bekommen: 
**Lesen**
Der Benutzer darf aus der Datei lesen oder, im Falle eines Verzeichnisses, seinen Inhalt auslesen, allerdings keine Dateirechte dieser Dateien erfahren. Dieses Recht wird oft durch den Buchstaben „r“ für englisch read („lesen“) dargestellt und daher auch R-Bit genannt.

**Schreiben**
Der Benutzer darf in die Datei schreiben bzw. Dateien und Unterverzeichnisse in dem Verzeichnis erstellen, umbenennen, löschen und deren Dateirechte verändern. Dieses Recht wird oft durch den Buchstaben „w“ für englisch write („schreiben“) dargestellt und daher auch W-Bit genannt.

**Ausführen**
Der Benutzer darf die Datei als Programm ausführen bzw. in das Verzeichnis wechseln und dort Dateien oder Unterverzeichnisse erreichen. Ohne das Lesen-Recht darf der Verzeichnisinhalt jedoch nicht ausgelesen werden. Dieses Recht wird oft durch den Buchstaben „x“ für englisch execute („ausführen“) dargestellt und daher auch X-Bit genannt.

#### Symbolische Notation
```
|                   | Eigentümer |  Gruppe  | Sonstige |
|    Leserecht      |   r - -    |  r - -   |  r - -   |
|  Schreibrecht     |   - w -    |  - w -   |  - w -   |
| Ausführungsrecht  |   - - x    |  - - x   |  - - x   |
```

Quelle: [https://de.wikipedia.org/wiki/Unix-Dateirechte]

------------------------------------------------------------------------------------------------------------------------

## Links
Hier sind alle Links aufgelistet die oben angegeben worden sind:

[Partitionen]: https://de.wikipedia.org/wiki/Partition
[Arten von Dateien]: https://de.wikipedia.org/wiki/Datei
[Mount / Unmount]: https://de.wikipedia.org/wiki/Mounten
[Symbolische Notation]: https://de.wikipedia.org/wiki/Unix-Dateirechte
