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

--------------------------
### Verzeichnisse unter Linux

```bash
michael@michael-GL752VW:/$ ls -l
insgesamt 2097256
drwxr-xr-x   2 root root       4096 Okt  8 19:44 bin
drwxr-xr-x   4 root root       4096 Okt  8 19:43 boot
drwxrwxr-x   2 root root       4096 Okt  7 18:41 cdrom
drwxr-xr-x  21 root root       5120 Okt 18 15:12 dev
drwxr-xr-x 124 root root      12288 Okt 17 20:13 etc
drwxr-xr-x   4 root root       4096 Okt 12 17:21 home
lrwxrwxrwx   1 root root         32 Okt  7 18:50 initrd.img -> boot/initrd.img-5.0.0-23-generic
lrwxrwxrwx   1 root root         32 Okt  7 18:50 initrd.img.old -> boot/initrd.img-5.0.0-23-generic
drwxr-xr-x  22 root root       4096 Okt 12 11:32 lib
drwxr-xr-x   2 root root       4096 Aug  5 20:58 lib64
drwx------   2 root root      16384 Okt  7 18:38 lost+found
drwxr-xr-x   3 root root       4096 Okt  7 19:07 media
drwxr-xr-x   2 root root       4096 Aug  5 20:58 mnt
drwxr-xr-x   3 root root       4096 Okt  7 19:13 opt
dr-xr-xr-x 337 root root          0 Okt 18 15:12 proc
drwx------   4 root root       4096 Okt 14 13:56 root
drwxr-xr-x  30 root root        900 Okt 18 16:44 run
drwxr-xr-x   2 root root      12288 Okt  8 19:42 sbin
drwxr-xr-x  16 root root       4096 Okt  7 20:20 snap
drwxr-xr-x   2 root root       4096 Aug  5 20:58 srv
-rw-------   1 root root 2147483648 Okt  7 18:39 swapfile
dr-xr-xr-x  13 root root          0 Okt 18 15:12 sys
drwxrwxrwt  17 root root       4096 Okt 18 16:44 tmp
drwxr-xr-x  11 root root       4096 Aug  5 21:03 usr
drwxr-xr-x  14 root root       4096 Aug  5 21:11 var
lrwxrwxrwx   1 root root         29 Okt  7 18:50 vmlinuz -> boot/vmlinuz-5.0.0-23-generic
```
**/etc**: Im Ordner etc findet man Dateien für die Systemsteuerung.<br>
**/root**: Home Verzeichniss des Super Users.<br>
**/home**: Im home Verzeichnis liegen die home Verzeichnisse aller Benutzer.<br>
**/boot**: Im boot Order liegen Dateien, die den Bootvorgang steuern.<br>
**/dev**: Im dev Ordner liegen Gerätdateien über die der Zugriff auf Geräte erfolgt.<br>
**/media**: Hier liegen die Gerätdateien von Wechselmedien(USB-Sticks, DVDs.)<br>
**/mnt**: Im mnt Verzeichnis liegen Geräte, die manuell temporär eingebunden wurden.<br>
**/bin** Im bin Verzeichnis liegen wichtige Systemprogramme.<br>
**/tmp**: Im tmp(temporär) Ordner liegen temporäre Dateien, die beim nächsten Systemstart gelöscht werden.<br>
**/run**: Hier liegen Dateien, die für laufende Programme wichtig sind.<br>
**/usr**: Unix System Resources<br>
**/var**: Hier liegen variable Daten.
**/proc und /sys**: sind virtuelle Verzeichnisse, über die der Benutzer direkt mit dem Kernel kommunizieren kann.
```bash
michael@michael-GL752VW:/$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 94
model name	: Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz
stepping	: 3
microcode	: 0xcc
cpu MHz		: 800.010
cache size	: 6144 KB
physical id	: 0
siblings	: 8
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 22
wp		: yes
...
```
--------------------------
### Einhängen von Dateisystemen
Laut [Linux-1](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/7BF1B31508DF3.symlink?resource_id=0-385942208&m=view#150959512)
>In Windows wird jedes unterstützte Dateisystem auf einem formatierten Datenträger bzw. einer Partition über einen Laufwerksbuchstaben als Verzeichniswurzel verfügbar gemacht. A: und B: sind für Floppy-Laufwerke vorgesehen. C: ist daher normaler­ weise das erste Festplatten-Dateisystem. Die Einbindung funktioniert automatisch.<br>
In Linux gibt es nur eine Verzeichniswurzel. Diese wird mit / (dem Slash) benannt.
Für Dateisysteme auf Floppy-Laufwerken, CD/DVD-Laufwerken, Festplatten, Netzlauf­ werken, ... wird ein Verzeichnis an einer beliebigen Stelle im Verzeichnisbaum erstellt, und dieses Verzeichnis, der mount-point, wird mit dem Dateisystem verbunden.
Wir sprechen vom „mounten eines Device“, zu deutsch „einhängen eines Geräts“. In aktuelle Linux-Desktop-Distributionen geschieht der Vorgang voll automatisch. Die Geräte sind unter dem Verzeichnis /media zu finden.

Die aktuell gemounteten Dateisysteme lassen sich mit dem Befehl mount anzeigen.
```bash
michael@michael-GL752VW:/$ mount
...
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
/dev/sdb1 on /media/816E-DD42 type vfat (rw,nosuid,nodev,uid=1000,gid=1000, ...)
/dev/sdc1 on /media/6F112B4136D46EAE type fuseblk (rw,nosuid, ...)
```
Die Informationen in den Klammern geben an in welchem Modus die Geräte eingebunden sind. Mehr Informationen findet man mit man mount.

#### Manuelles Einhängen von Geräten



 
