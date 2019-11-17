# 2. Protokoll m17-3AHME-la1-sx
--------------------------------
### Erstellt:
* 16.11.2019
* Mike Adam
--------------------------------
## Inhaltsverzeichnis:
1) [Die Linux Shell](#die-linux-shell)
2) [Arbeiten mit der Shell](#arbeiten-mit-der-shell)
3) [SSH](#ssh)
   * [Autovervollständigung](#autovervollständigung)
   * [Kommandos durchblättern](#kommandos-durchblättern)
   * [Cursor bewegen](#cursor-bewegen)
   * [Grundlegende Kommandos](#grundlegende-kommandos)
   * [Suchmuster für Dateien](#suchmuster-für-dateien)
4) [Einen neuen Benutzer anlegen](#einen-neuen-benutzer-anlegen)
5) [Dateirechte](#dateirechte)



## Die Linux Shell:
Ist ein Linux Programm, das Kommandos über die Tastatur aufnimmt und als Befehle wertet und ausführt. Mit der Shell kann man einen PC   vollständig steuern.
* Keine GUI nötig
* Effizientes arbeiten
* Fernsteuerung möglich (Fernwartung)
* Befehle und Befehlsketten sind leicht dokumentierbar
* Grundwissen erforderlich

## Arbeiten mit der Shell:

### Autovervollständigung:
* Mit der **Tabulator** Taste kann man das Kommando, dass noch nicht komplett ausgeschrieben ist vervollständigen um Felher bei der Eingabe zu vermeiden

### Kommandos durchblättern: 
* Mit den **Pfeiltasten** ⇧ und ⇩ kann man ältere Kommandos aufrufen, um sie nicht nochmal eingeben zu müssen

### Cursor bewegen:
* den Cursor kann man mit den **Pfeiltasten** ⇦ und ⇨ bewegen

### Andere Shortcuts:

       Strg + Shift + c ... Kopieren in Zwischenablage
       Strg + Shift + v ... Einfügen aus Zwischenablage
       Strg + r ... Suchen nach früheren Kommandos
       Strg + l ... Löschen des Bildschirms
       Strg + c ... Abbrechen eines Kommandos
       Strg + z ... Pausieren eines Kommandos
       Strg + d ... Shell beenden (detach)
       Strg + t ... Die Zeichen unter dem Cursor tauschen
       
       
### Grundlegende Kommandos:

      pwd      print working directory  
      ls       list directory content
                 ls                      -> Dateien und Verzeichnisse von ./ ausgegeben
                 ls -l                   -> Line-Mode, mehr Infos anzeigen
                 ls -a                   -> all, auch verborgene Dateien anzeigen
                 ls -L                   -> Link anwenden und nicht anzeigen
      cd       change directory          In ein (anderes) Verzeichnis wechseln
      touch    touch file                Leere Datei anlegen oder Zeitstempel ändern
      mkdir    make directory            Verzeichnis erstellen
      mv       move                      Datei/Verzeichnis verschieben oder umbenennen
      cp       copy                      Date/Verzeichnis kopie
      scp      secure copy               copy über Netzwerk via ssh (secure shell)
      rm       remove                    Datei oder löschen
      rmdir    remove directory          Verzeichnis löschen (muss leer sein!)
      ln       link                      Links erstellen
      cat      concatenate               Dateien verbinden und auf stdout ausgeben
      less     less (is more)            Dateiinhalt im Viewer less anzeigen
      hexdump  hexadecimal file dump     Dateiinhalt als Hexdump ausgeben
      grep     global search for a       Auf ein Suchmuster passende Zeilen ausgeben
      find     find files                Dateien oder Verzeichnisse finden
      dd       duplicate data            Daten 1:1 kopieren (auch auf Geräte anwendbar) 
      df       disk free space           Freien Speicher auf Dateisystemen anzeigen
      du       disk usage                Byte-Verbrauch in Verzeichnis(sen) zeigen
      mount    mount a filesystem        Partition einbinden
      umount   unmount a filesystem      Eingebundene Partition trennen
   
### Suchmuster für Dateien:
       * für beliebige Zeichen
       ? für ein beliebiges Zeichen
       [] für passende Zeichen ( p[abc].txt → pa.txt pb.txt pc.txt)
       {} für passende Textstücke ( p{rot,gruen}.txt → prot.txt pgruen.txt)
       ~ für das Home-Verzeichnis
       . für das aktuelle Verzeichnis
       .. für das übergeordnete Verzeichnis

## SSH:
>Secure Shell oder SSH bezeichnet sowohl ein Netzwerkprotokoll als auch entsprechende Programme, mit deren Hilfe man auf eine sichere Art und Weise eine verschlüsselte Netzwerkverbindung mit einem entfernten Gerät herstellen kann. Häufig wird diese Methode verwendet, um lokal eine entfernte Kommandozeile verfügbar zu machen, das heißt, auf einer lokalen Konsole werden die Ausgaben der entfernten Konsole ausgegeben und die lokalen Tastatureingaben werden an den entfernten Rechner gesendet. Genutzt werden kann dies beispielsweise zur Fernwartung eines in einem entfernten Rechenzentrum stehenden Servers. Die neuere Protokoll-Version SSH-2 bietet weitere Funktionen wie Datenübertragung per SFTP.

Quelle: [Wikipedia][Wikipedia - SSH]


## Einen neuen Benutzer anlegen:

Einen neuen Benutzer kann man mit folgenden Kommandos anlegen:
1) **Wechseln zum Superuser** (Kommando: sudo -i)
2) **"passwd" Textdatei bearbeiten** (Kommando: nano /etc/passwd/)
3) **Erstellen des "Home" Verzeichnis** (Kommando: mkdir/home/"Benutzer")
4) **Besitzer am "Home" Verzeichnis ändern** (Kommando: chown name /home/"Besitzer")
5) **Bearbeiten der "group" Datei** (Kommando: nano /etc/group)
6) **Ändern der Gruppe** (Kommando: chgrp name /home/name)
7) **Bearbeiten der "shadow" Datei** (Kommando: nano /etc/shadow)

## Dateirechte:

**es werden diese Eigenschaften bei einer Datei verwaltet:**
* Besitzer
* Gruppe
* Dateityp
* Zugriffsrechte

**Beispiel:**
      
      -rwxr-x--- 1 besitzer gruppe 1245 Mär 19 10:54 test.dat
      
      
* **r  ... read**
Der Verzeichnisinhalt darf gelesen werden
* **w  ... write**
Im Verzeichnis dürfen neue Dateien angelegt oder bestehende Dateien gelöscht werden
* **x  ... execute**
Es darf in den Verzeichnisse auf die Dateieigenschaften und auf Unterverzeichnisse zugegriffen werden

![](https://www.webhostone.de/images/FAQ/Webpakete/dateirechte3.png)

Abbildung der Benutzer und Dateirechte:





[Wikipedia - SSH]: https://de.wikipedia.org/wiki/Secure_Shell
