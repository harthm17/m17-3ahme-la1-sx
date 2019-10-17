# Protokoll LA1 / 3AHME (2019/20)
* **Thema:** Partitionen, Dateien und Verzeichnisse (Linux) / Shell
* **Datum:** 14.10.2019
* **Gefehlt:** ---
* **Erstellt von:** strrim17
* **Protokoll letzte Einheit:**
* **Protokoll nächste Einheit:**

------------------------------------------------------------------------------------------------------------------------

## Inhaltsverzeichnis

1. [Linux](#linux)
   1. [Linux als Betriebssystem](#linux-als-betriebssystem)
   2. [Partitionen](#partitionen)
   3. [Dateien](#dateien)
      1. [Dateisysteme](#dateisysteme)
      2. [Arten von Dateien](#arten-von-dateien)
   4. [Verzeichnisse](#verzeichnisse)
      1. [Ordner](#ordner)
2. [Shell](#shell)
   1. [Was ist eine Shell](#was-ist-eine-shell)
   2. [Erste Schritte](#erste-schritte)
   3. [Aufbau der Kommandos](#aufbau-der-kommandos)


------------------------------------------------------------------------------------------------------------------------

## Linux
Laut Wikipedia:

Als Linux oder GNU/Linux bezeichnet man in der Regel freie, unixähnliche Mehrbenutzer-Betriebssysteme, die auf dem Linux-Kernel und wesentlich auf GNU-Software basieren.

Das modular aufgebaute Betriebssystem wird von Softwareentwicklern auf der ganzen Welt weiterentwickelt, die an den verschiedenen Projekten mitarbeiten. Beim Gebrauch auf Computern kommen meist sogenannte Linux-Distributionen zum Einsatz. Eine Distribution fasst den Linux-Kernel mit verschiedener Software zu einem Betriebssystem zusammen, das für die Endnutzung geeignet ist. Dabei passen viele Distributoren und versierte Benutzer den Kernel an ihre eigenen Zwecke an.

Linux wird vielfältig und umfassend eingesetzt, beispielsweise auf Arbeitsplatzrechnern, Servern, Mobiltelefonen, Routern, Netbooks, Embedded Systems, Multimedia-Endgeräten und Supercomputern. Dabei wird Linux unterschiedlich häufig genutzt: So ist Linux im Server-Markt wie auch im mobilen Bereich eine feste Größe, während es auf dem Desktop und Laptops eine noch geringe, aber wachsende Rolle spielt.

Quelle: [https://de.wikipedia.org/wiki/Linux]

### Linux als Betriebssystem
Ein Betriebssystem ist eine Zusammenstellung von Computerprogrammen, die die Systemressourcen eines Computers wie Arbeitsspeicher, Festplatten, Ein- und Ausgabegeräte verwaltet und diese Anwendungsprogrammen zur Verfügung stellt. Das Betriebssystem bildet dadurch die Schnittstelle zwischen den Hardwarekomponenten und der Anwendungssoftware des Benutzers.

Betriebssysteme bestehen in der Regel aus einem Kernel, der die Hardware des Computers verwaltet, sowie speziellen Programmen, die beim Start unterschiedliche Aufgaben übernehmen. Zu diesen Aufgaben gehört unter anderem das Laden von Gerätetreibern.

### Partitionen
Ein Datenträger kann mit Hilfe der Partitionierung in mehrere Teile, sogenannte Partitionen, getrennt werden.
Diese Partitionen werden von Linux als Block-Device im Verzeichnis /dev zur Verfügung gestellt.
Dabei gilt folgende Namensgebung:

* SCSI und S-ATA Datenträger bekommen die Kennung sd (scsi-drive, s-ata drive):
  Jeder reale Datenträger bekommt zusätzlich zu sd einen Buchstaben: 1.Datenträger = sda, 2. Datenträger = sdb, 3. Datenträger = sdc,   ...
  Jede Partition bekommt zusätzlich eine Zahl
  Beispiel: /dev/sda1 (= 1 Partition am 1.Datenträger)

* Flash-Speicherkarten bekommen die Kennung mcblk
  Jedes Medium bekommt eine Nummer, die Partitionen werden mit p0, p1, ... nummeriert.
  Beispiel: /dev/mmcblk0p1

Beispiel: /dev/sda3 ist das Gerät (Block-Device) über das die 3. Partition am 1. Datenträger (interne Festplatte) angesprochen werden kann.
Partitionen können mit Hilfe des Befehls mount in den Verzeichnisbaum an beliebiger Stelle eingebunden werden. 
Viele Linux Distributionen erledigen diese Aufgabe automatisch. Spezielle Wünsche können mit Hilfe der Datei /etc/fstab (file system table) realisiert werden. Zum Beispiel, dass ein spezielle Flash-Speicher nur lesbar eingebunden wird.

Beim Raspberry PI hat die Datei /etc/fstab folgenden Aufbau:

```
proc            /proc           proc    defaults          0       0
/dev/mmcblk0p1  /boot           vfat    defaults          0       2
/dev/mmcblk0p2  /               ext4    defaults,noatime  0       1
```

Die erste Partition am Flash-Speicher wird als /boot eingebunden. Die zweite Partition ist die Verzeichniswurzel.

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
Eine Datei ist ein Bestand meist inhaltlich zusammengehöriger Daten, der auf einem Datenträger oder Speichermedium gespeichert ist. Diese Daten können somit über die Laufzeit eines Programms hinaus existieren und werden als persistent bezeichnet – sie sind bei Programmende nicht verloren.

In der elektronischen Datenverarbeitung ist der Inhalt jeder Datei zunächst eine eindimensionale Aneinanderreihung von Bits, die normalerweise in Byte-Blöcken zusammengefasst interpretiert werden. Erst der Anwender einer Datei bzw. ein Anwendungsprogramm oder das Betriebssystem selbst interpretieren diese Bit- oder Bytefolge beispielsweise als einen Text, ein ausführbares Programm, ein Bild oder eine Tonaufzeichnung. Eine Datei besitzt also ein Dateiformat.

#### Dateisysteme
Dateien werden in den meisten Betriebssystemen über Dateisysteme verwaltet. Ein Dateisystem verwaltet das Speichermedium, indem in Listen vermerkt wird, welche Bereiche des Mediums durch welche Dateien belegt sind, welche Bereiche frei sind, sowie oft Protokolle zu geplanten und/oder abgeschlossenen Änderungen.

Das Dateisystem verwaltet neben Verzeichnissen mit Dateinamen und -speicherort fast immer noch weitere Dateiattribute. Zu diesen gehören häufig der Dateityp (Verzeichnis, normale Datei, spezielle Datei), die Dateigröße (Anzahl der Bytes in der Datei), Schreib- und Leserechte, Zeitstempel („Datum“, der Erzeugung, des letzten Zugriffs und der letzten Änderung) sowie gegebenenfalls noch andere Informationen. Eine Datei kann in vielen Dateisystemen durch ein Attribut als versteckte Datei gekennzeichnet werden.

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
Ein Verzeichnis oder Register, auch Katalog, Ordner oder Auflistung, in Österreich Evidenz genannt, ist eine listenförmig darstellbare Anordnung von Informationen nach bestimmten Merkmalen.

#### Ordner
Die Worte Ordner und Verzeichnisse haben leicht unterschiedliche Bedeutungen, obwohl sie oft für die gleiche Sache verwendet werden. Wenn man einen Behälter für Dokumente meint, ist der Begriff Ordner besser geeignet. Der Begriff Verzeichnis bezieht sich auf eine strukturierte Liste von Dokumenten, Dateien und Ordnern auf dem Computer. Ein Verzeichnis ist mit einem Telefonbuch vergleichbar, das Namen, Telefonnummern und Adressen enthält, aber nicht die eigentlichen Häuser selbst.

Quelle: [https://de.wikipedia.org/wiki/Verzeichnis]

------------------------------------------------------------------------------------------------------------------------
