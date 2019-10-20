# 2.Protokoll Labor/SX 3AHME (2019/20)

* Thema: Datenträger, DLL, Linux Shell
* Datum: 14.10.2019
* Gefehlt: Niemand
* Erstellt von: Georg Schnabel
* Protokoll letzte Einheit: [1.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/snagem17/protokoll_2019-09-30_snagem17.md)

## Inhaltsverzeichnis
1. [Datenträger](https://de.wikipedia.org/wiki/Datenspeicher)
* [Partition](https://de.wikipedia.org/wiki/Partition_(Datenträger))
2. [DLL](https://de.wikipedia.org/wiki/Dynamic_Link_Library)
* [DLL Hölle](https://de.wikipedia.org/wiki/DLL-Konflikt)
3. [Linux Shell](https://de.wikipedia.org/wiki/Bash_(Shell))
* Befehle
4. Rechte
5. [Verzeichnisse](https://de.wikipedia.org/wiki/Verzeichnisstruktur)


## Datenträger
[Datenträger](https://de.wikipedia.org/wiki/Datenspeicher) laut Wiki:

>Ein Datenspeicher oder Speichermedium dient zur Speicherung von Daten. Der Begriff Speichermedium wird auch als Synonym für einen konkreten Datenträger verwendet. 
>Im engeren Sinne bezeichnet man mit Datenträger oder Speichermedium Medien, die als Datenspeicher dienen 
>1. für Unterhaltung (Musik, Sprache, Film etc.), die mit Hilfe elektronischer Geräte abgespielt oder auch gespeichert wird; und
>2. für Daten jeglicher Art (auch Unterhaltung), die von Computern bzw. Computeranlagen oder Peripheriegeräten nur gelesen oder auch       geschrieben werden.

Mit Datenträger können Daten in Form von [Bitketten](https://de.wikipedia.org/wiki/Bitkette) gespeichert werden. 
[Bitketten](https://de.wikipedia.org/wiki/Bitkette) werden in der Einheit Byte angegeben (1Byte = 8 Bit). Datenträger können sehr viele Bytes speichern, meist werden sie in Gigabyte oder Terrabyte angegeben.

### Partition
Wenn man einen Datenträger [partitioniert](https://de.wikipedia.org/wiki/Partition_(Datenträger)) bedeutet das, dass man ihn in mehrer Teile aufteilt. Das ist ein sehr wichtige Vorgang, da [Dateisysteme](https://de.wikipedia.org/wiki/Dateisystem) erst nach dem Partitionieren [formatiert](https://de.wikipedia.org/wiki/Formatierung) und eingebunden werden können.

## DLL
[DLL](https://de.wikipedia.org/wiki/Dynamic_Link_Library)
>Dynamic Link Library (DLL) bezeichnet allgemein eine dynamische Programmbibliothek; meist bezieht sich der Begriff jedoch auf die für die Betriebssysteme Microsoft Windows und OS/2 verwendete Variante. 
DLL-Dateien verwenden das auch für ausführbare EXE-Dateien gebräuchliche Dateiformat, das in 16-Bit-Programmen das New-Executable-Format (NE)[1] und in 32- und 64-Bit-Programmen das Portable-Executable-Format (PE) ist. Diese Dateien können Programmcode (Maschinencode), Daten und Ressourcen in beliebiger Kombination enthalten.

**DLL** = (Dynamic Link Library) sind sogennannte so-Dateien (Static Optic File) und dienen dazu, den Speicher möglichst wenig zu belasten.

### DLL-Hölle
Mit [DLL-Hölle](https://de.wikipedia.org/wiki/DLL-Konflikt) werden Probleme bezeichnet, die nach der Installation von [DLLs](https://de.wikipedia.org/wiki/Dynamic_Link_Library) am Betriebssystem auftreten und nur schwer lösbar sind.

Quelle: [Wiki](https://de.wikipedia.org/wiki/DLL-Konflikt)
>Der Ausdruck DLL-Konflikt (auch DLL Hell, deutsch: „DLL-Hölle“ genannt) bezeichnet ein Problem, das durch die Installation von Dynamic Link Library (DLLs) auf den Betriebssystemen der Windows-Reihe entstehen kann. Vorwiegend sind ältere Windowsversionen betroffen, da diese nur beschränkte Möglichkeiten besitzen, um System-Dateien und DLL-Bibliotheken zu verwalten.

## Linux Shell

### Gerät ein-/aushängen
Mit [mount](https://wiki.ubuntuusers.de/mount/#Dateisysteme-einbinden) kann man das Gerät einhängen, jedoch sind hinter dem mount noch weitere Kommandos nötig.


Mit [umount](https://wiki.ubuntuusers.de/mount/#Dateisysteme-aushaengen) kann das Gerät wieder ausgehängt werden.

### Neuer Benutzer
Zuerst muss man zum Superuser werden
```
sudo -i = man wird zum Superuser (Superuser root)
```
```
nano/etc/passwd
nano/etc/group
nano/etc/shadow
```
##  Rechte

Rechte in der EDV, dienen zum Regeln, wer die Dateien lesen, schreiben, ändern oder ausführen darf. Es wird zwischen **Eigentümer=user=u**, **Gruppe=group=g** und **Alle anderen=others=o** unterschieden.

![Bild](https://upload.wikimedia.org/wikipedia/de/1/19/Zugriffsrecht.png)

Es gibt 3 verschiedene Rechte: 

**Datei:**                                        
* r = read(lesen)                                
* w = write(schreiben,modifizieren)               
* x = execute(ausführen)                          

**Verzeichnis:**
* r = Inhalt sehen
* w = Inhalt veränderbar
* x = In das Verzeichnis wechseln

**Beispiel:**
0=nicht zulässig
1=zulässig

* uuu ggg ooo
* rwx rwx rwx
* 110 100 000 = Dateirechte

Dieses Beispiel würde jetzt bedeuten, dass der User (Eigentümer) die Datei lesen und verändern darf aber nicht ausführen darf und dass die Gruppe lesen darf. Alle anderen dürfen mit der Datei gar nichts machen.

## Verzeichnisse
