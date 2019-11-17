# Protokoll m17-3ahme-la1
* **Datum:** 17.11.2019
* **Erstellt von:** Danko Sebastian
---------------------------------------

## Inhaltsverzeichniss

1. [Die Secure Shell](#Die-Secure-Shell)
1. [Funktionen](#funktionen)
1. [Suchmuster für Dateien](#Suchmuster-für-Dateien)
1. [Kommandos](#kommandos)
1. [Berechtigungen](#berechtigungen)
1. [Benutzer anlegen](#benutzer-anlegen)
--------------------------------------------------------------

## Die Secure Shell
>Der Begriff "SSH" bezeichnet einerseits ein Netzwerkprotokoll und andererseits das dazu passende Programm. Mit der Secure Shell SSH ist es möglich eine sichere (verschlüsselte) Verbindung zwischen zwei Rechnern aufzubauen. SSH ersetzt das Vorgängersystem Telnet.
Seit 1996 wird mit der Protokoll-Version SSH-2 gearbeitete. Die Vorgängerversion SSH-1 ist nicht mehr sicher und sollte nicht mehr verwendet werden. Seit 2005 existiert auch die dritte Generation SSH G3.
Bei der Verschlüsselung kommt ein hybrides Verfahren zur Anwendung. In der Verbindungsphase kommt es mit Hilfe eines asymmetrischen Verfahrens (zB RSA) zum Austausch eines Schlüssels, der dann mit Hilfe eines sysmmtrischen Verfahrens (zB AES) die Verschlüsselung großer Datenmengen erlaubt.
Bei Linux ist SSH die zentrale Methode um eine Shell auf einem entfernten Rechner zu starten.
Auf Windows-Rechnern wird häufig das Programm PuTTY verwendet um sich via SSH mit einem entfernten Linux Rechner zu verbinden.

Quelle: [LMS][lms1] (Stand: 17.11.2019)
---------------------------------------------------------------

##  Funktionen:
• Strg + Shift + c ... Kopieren in Zwischenablage<br>
• Strg + Shift + v ... Einfügen aus Zwischenablage<br>
• Strg + r ... Suchen nach früheren Kommandos<br>
• Strg + l ... Löschen des Bildschirms<br>
• Strg + c ... Abbrechen eines Kommandos<br>
• Strg + z ... Pausieren eines Kommandos<br>
• Strg + d ... Shell beenden (detach)<br>
• Strg + t ... Die Zeichen unter dem Cursor tauschen<br>

Quelle: [LMS][lms2] (Stand: 17.11.2019)
--------------------------------------------------------------------

## Suchmuster für Dateien
• * für beliebige Zeichen<br>
• ? für ein beliebiges Zeichen<br>
• [] für passende Zeichen ( p[abc].txt → pa.txt pb.txt pc.txt)<br>
• {} für passende Textstücke ( p{rot,gruen}.txt → prot.txt pgruen.txt)<br>
• ~ für das Home-Verzeichnis<br>
• . für das aktuelle Verzeichnis<br>
• .. für das übergeordnete Verzeichnis<br>

Quelle: [LMS][lms2] (Stand: 17.11.2019)
---------------------------------------------------------------------

## Kommandos:
### Dateien/Verzeichnisse<br>
Befehl   | Bedeutung                | Erklärung<br>
|--------|--------------------------|---------------------------------------------
pwd      | print working directory  | Aktuelles Arbeitsverzeichnis (.) ausgeben<br>
ls       | list directory content   | Dateien und Verzeichnisse von ./ ausgegeben<br>
cd       |change directory          | In ein (anderes) Verzeichnis wechseln<br>
touch    | touch file               | Leere Datei anlegen oder Zeitstempel ändern<br>
mkdir    |make directory            | Verzeichnis erstellen<br>
mv       |move                      | Datei/Verzeichnis verschieben oder umbenennen<br>
cp       |copy                      | Date/Verzeichnis kopieren<br>
rm       |remove                    | Datei oder löschen<br>
rmdir    |remove directory          | Verzeichnis löschen (muss leer sein!)<br>
ln       |link                      | Links erstellen<br>
cat      |concatenate               | Dateien verbinden und auf stdout ausgeben<br>
less     |less (is more)            | Dateiinhalt im Viewer less anzeigen<br>
hexdump  |hexadecimal file dump     | Dateiinhalt als Hexdump ausgeben<br>
grep     |global search for a       | Auf ein Suchmuster passende Zeilen ausgeben<br>
find     |find files                | Dateien oder Verzeichnisse finden<br>
dd       |duplicate data            | Daten 1:1 kopieren (auch auf Geräte anwendbar) <br>
df       |disk free space           | Freien Speicher auf Dateisystemen anzeigen<br>
du       |disk usage                | Byte-Verbrauch in Verzeichnis(sen) zeigen<br>
mount    |mount a filesystem        | Partition einbinden<br>
umount   |unmount a filesystem      | Eingebundene Partition trennen<br>
Quelle: [LMS][lms] (Stand: 17.11.2019)
### Betriebssystem und Prozesse
Befehl   | Bedeutung                | Erklärung<br>
|--------|--------------------------|---------------------------------------------
date         |print system date and time  |  Aktuelle Zeit ausgeben
lsb_release  |linux standard base ...     |  Infos über die Distribution ausgeben
uptime       |how long the system ...     |  Seit wann läuft das System und ...
dpkg         |debian package              |  Paketverwaltung für Debian
top          |display linux processes     |  Linux Prozesse anzeigen (Ende mit Taste q)
ps           |process status              |  Prozessdetails anzeigen
jobs         |show user processes         |  Eigene Prozesse anzeigen
kill         |kill/signal process         |  Signal an Prozess senden, Prozess beenden 
free         |display free/used memory    |  Arbeitsspeicher (RAM) anzeigen 

Quelle: [LMS][lms] (Stand: 17.11.2019)
### Benutzerverwaltung<br>
Befehl   | Bedeutung                |     Erklärung<br>
|--------|--------------------------|---------------------------------------------
whoami   |   who am i               |     aktuellen Benutzer ausgeben
who      |   who is logged on       |     wer ist gerade angemeldet
w        |   who is logged on and . |     wer ist wie angemeldet
passwd   |   set new password       |     Passwort neu setzen
su       |   set (change) user id   |     andere Benutzer-ID annehmen
sudo     |   super-user do          |     in den Super-User Mode (root) wechseln
login    |   login with new session |     startet eine neue Session im System
id       |   display user id ...    |     Benutzerinfos anzeigen
groups   |   display groups         |     Gruppenmitgliedschaft anzeigen
adduser  |   add new user           |     Neuen Benutzer hinzufügen
deluser  |   delete user            |     Benutzer entfernen

Quelle: [LMS][lms] (Stand: 17.11.2019)
-----------------------------------------------------------------------------------------------
## Berechtigungen:
Abbildung 1 ![](http://www.easylinux.de/Artikel/ausgabe/2003/09/071-guru-chmod/rwx-grafix_s.jpg)
>Dateirechte regeln, welcher Benutzer was mit einer Datei darf. Dabei ist zu beachten, dass echter Schutz nur mit Verschlüsselung oder durch Platzierung des Rechners in einem unzugänglichen Raum gegeben ist!
Folgende Eigenschaften einer Datei werden verwaltet:<br>
Dateityp
Besitzer
Gruppe
Zugriffsrechte
Alle in Linux gängigen Dateisystem (ext4, ...) unterstützen diese Eigenschaften. Bei Dateisystemen der Windows-Welt (VFAT, NTFS, ...) sind diese Eigenschaften hingegen nur teilweise oder gar nicht umgesetzt. Daher kann es beim Arbeiten mit solchen Verzeichnissen auch zu Problemen kommen, für dessen Lösung Expertenwissen erforderlich ist.
Angezeigt werden Dateityp und Eigenschaften in der Shell mit Hilfe des Kommandos ls unter Verwendung der

Quelle: [LMS][lms3] (Stand: 17.11.2019)
----------------------------------------------------------------------------------------------------------

## Benutzer anlegen

1. Wecheln zum Superuser__________________(sudo -i)<br>
1. Die passwd Datei bearbeiten_____________(nano /etc/passwd/)<br>
1. Passwort eingeben_______________________(sudo passwd name)<br>
1. Erstellen des Home Verzeichnis__________(mkdir/home/name)<br>
1. Besitzer vom Home Verzeichnis ändern__(chown name /home/name)<br>
1. Group Datei Bearbeiten__________________(nano /etc/group)<br>
1. Gruppe des Benutzer's wechseln_________(chgrp name /home/name)<br>
1. Die shadow datei bearbeiten_____________(nano /etc/shadow)<br>






[lms]: https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/7BF1B31508DF3.symlink?resource_id=0-385942208&m=view#154334970
[lms1]:https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/7BF1B31508DF3.symlink?resource_id=0-385942208&m=view#160116878
[lms2]:https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/7BF1B31508DF3.symlink?resource_id=0-385942208&m=view#150960483
[lms3]:https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/7BF1B31508DF3.symlink?resource_id=0-385942208&m=view#155471000
