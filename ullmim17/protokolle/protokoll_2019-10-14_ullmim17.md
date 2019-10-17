# Protokoll La1/SX 3AHME (2019/20)
--------------
 * **Thema:** Github und Markdown
  * **Datum:** 14.10.2019
  * **Gefehlt:** ---
  * **Erstellt von:** Michael Ully 
  --------------------------------------------------
  ## Inhaltsverzeichnis
  -------------------------------------------------------
  ## Partitionen <br>
  
  Laut 
  [Wikipedia](https://de.wikipedia.org/wiki/Partition_(Datenträger))
  > Als Partition (lateinisch partitio ‚(Ein)teilung‘) wird ein zusammenhängender Teil eines Speicherplatzes eines geeigneten physischen bzw. eines logischen Datenträgers bezeichnet. Eine Partition ist ihrerseits ein logischer Datenträger, es gibt jedoch noch weitere Arten logischer oder virtueller Datenträger.Partitionen sind voneinander weitgehend unabhängig und können von Betriebssystemen wie getrennte Laufwerke behandelt werden. Man bezeichnet eine Partition daher auch oft als logisches Laufwerk. Der Zugriff auf die gespeicherten Daten obliegt dem Betriebssystem, das die Daten in den meisten Fällen über ein Dateisystem verwaltet: Die meisten Betriebssysteme ordnen jedem logischen Laufwerk genau ein Dateisystem zu; die meisten Dateisysteme erwarten, dass sie eine komplette Partition alleine verwalten.
  ---------------------------
  Dateisysteme
  --------------------------
Laut 
[Wikipedia](https://de.wikipedia.org/wiki/Dateisystem)
> Das Dateisystem (englisch file system oder filesystem) ist eine Ablageorganisation auf einem Datenträger eines Computers. Dateien können gespeichert, gelesen, verändert oder gelöscht werden. Für den Nutzer müssen Dateiname und computerinterne Dateiadressen in Einklang gebracht werden. Das leichte Wiederfinden und das sichere Abspeichern sind wesentliche Aufgaben eines Dateisystems. Das Ordnungs- und Zugriffssystem berücksichtigt die Geräteeigenschaften und ist normalerweise Bestandteil des Betriebssystems.

Dateien in einem Dateisystem haben faster immer einen Namen und Attribute, die nähere Informationen über die Datei preisgeben. Dateinamen sind in Verzeichnissen abgelegt. [Verzeichnisse](https://de.wikipedia.org/wiki/Verzeichnisstruktur) sind spezielle Dateien. Über Verzeichnisse kann ein Dateiname vom System gefunden werden. Alle Dateien sind so über eine eindeutige Adresse (Dateiname inkl. Pfad oder [URI](https://de.wikipedia.org/wiki/Uniform_Resource_Identifier)) – innerhalb des Dateisystems – aufrufbar. 

Unter Windows wird zum Beispiel das Dateisystem [NTFS](https://de.wikipedia.org/wiki/NTFS)(New Technology File System)verwendet, unter Linux [ext4](https://de.wikipedia.org/wiki/Ext4).

Mit dem Tool GParted kann man Partitionen erstellen, löschen und editieren.

### Arten von Dateisystemen 
#### Lineare Dateisysteme
Die historisch ersten Dateisysteme waren lineare Dateisysteme auf Lochband oder Lochkarte sowie die noch heute für die Sicherung von Daten eingesetzten Magnetbandsysteme.
#### Hierarchische Dateisysteme
Frühe Dateisysteme hatten nur ein einzelnes Verzeichnis, das dann Verweise auf alle Dateien des Massenspeichers enthielt. Mit wachsender Kapazität der Datenträger wurde es immer schwieriger, den Überblick über hunderte und tausende Dateien zu bewahren, deshalb wurde das Konzept der Unterverzeichnisse eingeführt. Ein hierarchisches Dateisystem wurde für das Betriebssystem Multics entwickelt und, nachdem dessen Entwicklung eingestellt wurde, von AT&T Unix Version 1 von 1971 übernommen. Damit war die Grundlage für die meisten modernen Dateisysteme gelegt, die im Wurzelverzeichnis neben regulären Dateien auch Verweise auf weitere Verzeichnisse, die Unterverzeichnisse, enthalten können, mit möglicherweise wiederum weiteren Unterverzeichnissen.

Dadurch entsteht eine Verzeichnisstruktur, die oft als Verzeichnisbaum dargestellt wird. Das Festplattenlaufwerk C: unter Windows beinhaltet beispielsweise neben Dateien wie boot.ini und ntldr auch Verzeichnisse wie Programme, Dokumente und Einstellungen usw. Ein Verzeichnis wie zum Beispiel Eigene Dateien kann dann wieder Unterverzeichnisse wie Eigene Bilder oder Texte enthalten. In Texte können dann beispielsweise die normalen Dateien Brief1.txt und Brief2.txt stehen.
 
 ![Dateisysteme](https://upload.wikimedia.org/wikipedia/de/thumb/1/1f/Filesystem.svg/800px-Filesystem.svg.png)
#### Mount
Der Befehl Mount zeigt an welche Partitionen bzw. Datenträger im Moment eingehängt(eng. mount) sind. 
