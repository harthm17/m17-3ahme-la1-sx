## Inhaltsverzeichnis
* [Linux Shell](#linux-shell)  
* [SSH](#ssh)  
* [Features](#features)  
* [Kommandos](#kommandos)  
* [Berechtigungen](#berechtigungen)  
* [Neuen Benutzer erstellen](#neuen-benutzer-erstellen)  
  
---------------------------------
## Linux Shell
> Weil die direkte Kommunikation mit dem Betriebssystem-Kern für einen Benutzer viel zu komplex wäre, ist eine vereinfachte
Benutzer-Schnittstelle erforderlich. Neben einer grafischen Schnittstelle wie dem X Window System wird diese Leistung vor allem
von einer Shell bereitgestellt. Der englische Ausdruck Shell, zu Deutsch etwa Schale oder Ummantelung, drückt diesen 
Sachverhalt bereits aus. Die Übersetzung oder Symbolisierung als Muschel hat dabei wohl mehr mit Spieltrieb und Anschaulichkeit
als mit einem echten technischen Hintergrund zu tun. Jedenfalls lässt sich eine Shell als eine Schicht zwischen Betriebssystem
und Benutzer verstehen. 
  
![](https://www.selflinux.org/selflinux/bilder/was_ist_shell_shell_funktionsweise01.png)
  
Quelle: [selflinux](https://www.selflinux.org/selflinux/html/was_ist_shell01.html)  
### Vorteile
* Effizienteres Arbeiten durch Verrkettung der Befehle
* Leicht dokumentierbare Befehle und Befehlsketten
* Fernwartung möglich
* Grundwissen gefordert
---------------------------------
## SSH
> Secure Shell oder SSH bezeichnet sowohl ein Netzwerkprotokoll als auch entsprechende Programme, mit deren Hilfe man auf
eine sichere Art und Weise eine verschlüsselte Netzwerkverbindung mit einem entfernten Gerät herstellen kann. Häufig wird
diese Methode verwendet, um lokal eine entfernte Kommandozeile verfügbar zu machen, das heißt, auf einer lokalen Konsole
werden die Ausgaben der entfernten Konsole ausgegeben und die lokalen Tastatureingaben werden an den entfernten Rechner
gesendet. Genutzt werden kann dies beispielsweise zur Fernwartung eines in einem entfernten Rechenzentrum stehenden Servers.
Die neuere Protokoll-Version SSH-2 bietet weitere Funktionen wie Datenübertragung per SFTP.
  
Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Secure_Shell)  
  
---------------------------------
## Features
Die Shell unterstützt den Benutzer in vielerei Hinsicht bei seiner Arbeit:  
* **Autovervollständigung**
    
        Durch Tippen der Tabulatortaste. Vorschläge können durch zweimaliges Tippen der Tabulatortaste angezeigt werden.
* **In früheren Kommandos blättern (History)**
    
        Mit den Pfeiltasten ⇧ und ⇩
* **Cursor bewegen**
    
        Mit den Pfeiltasten ⇦ und ⇨ horizontal bewegen.
        Den Cursor zum Anfang (Pos1 oder Strg+a) oder Ende (Ende oder Strg+e) der Zeile bewegen.
* **Weitere Funktionen:**
    
        - Strg + Shift + c ... Kopieren in Zwischenablage
        - Strg + Shift + v ... Einfügen aus Zwischenablage
        - Strg + r ... Suchen nach früheren Kommandos
        - Strg + l ... Löschen des Bildschirms
        - Strg + c ... Abbrechen eines Kommandos
        - Strg + z ... Pausieren eines Kommandos
        - Strg + d ... Shell beenden (detach)
        - Strg + t ... Die Zeichen unter dem Cursor tauschen
        - ...
* **Verwendung von Variablen**
    
        MEINEDATEI="/home/user/hallo.txt"
        cat $MEINEDATEI
* **Auführen von Kommandos im Hintergrund**
    
        (& am Ende)
* **Suchmuster für Dateien**
    
        - * für beliebige Zeichen
        - ? für ein beliebiges Zeichen
        - [] für passende Zeichen ( p[abc].txt → pa.txt pb.txt pc.txt)
        - {} für passende Textstücke ( p{rot,gruen}.txt → prot.txt pgruen.txt)
        - ~ für das Home-Verzeichnis
        - . für das aktuelle Verzeichnis
        - .. für das übergeordnete Verzeichnis
* **Verkettung von Kommandos** mit dem Pipe Operator `|`
* **Bedingte Verkettung** von Kommandos mit dem `&&` und `||` Operator
* **Mehrere Kommandos in einer Zeile** mit dem `;` als Trennzeichen
    
        Beispiel: echo $PATH; ls -al  
        
Quelle: [LMS](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/7BF1B31508DF3.symlink?resource_id=0-385942208&m=view#150960483)  
  
---------------------------------
## Kommandos
### Kommandos für Dateien/Verzeichnisse
**Symbol** | **Englisch** | **Deutsch**
---------- | ---------- | ----------
**pwd** |      print working directory |  Aktuelles Arbeitsverzeichnis (.) ausgeben
**ls** |      list directory content | Dateien und Verzeichnisse von ./ ausgegeben
**cd**  |    change directory       |   In ein (anderes) Verzeichnis wechseln
**touch** |    touch file        |        Leere Datei anlegen oder Zeitstempel ändern
**mkdir** |   make directory     |       Verzeichnis erstellen
**mv**    |   move              |        Datei/Verzeichnis verschieben oder umbenennen
**cp**   |    copy           |           Date/Verzeichnis kopieren
**scp**  |    secure copy     |          copy über Netzwerk via ssh (secure shell)
**rm**   |    remove             |       Datei oder löschen
**rmdir** |   remove directory     |     Verzeichnis löschen (muss leer sein!)
**ln**   |    link               |       Links erstellen
**cat**   |   concatenate        |       Dateien verbinden und auf stdout ausgeben
**less**   |  less     |       Dateiinhalt im Viewer less anzeigen
**hexdump** | hexadecimal file dump |    Dateiinhalt als Hexdump ausgeben
**grep**   |  +  |    Auf ein Suchmuster passende Zeilen ausgeben
**find** |    find files           |     Dateien oder Verzeichnisse finden
**dd**   |    duplicate data      |      Daten 1:1 kopieren (auch auf Geräte anwendbar) 
**df**   |    disk free space     |      Freien Speicher auf Dateisystemen anzeigen
**du**   |    disk usage           |     Byte-Verbrauch in Verzeichnis(sen) zeigen
**mount**  |  mount a filesystem    |    Partition einbinden
**umount**  | unmount a filesystem   |   Eingebundene Partition trennen    
  
### Kommandos für Betriebssystem und Prozesse  
**Symbol** | **Englisch** | **Deutsch**
---------- | ---------- | ----------  
**date**   |      print system date and time |   Aktuelle Zeit ausgeben  
**lsb_release** |   linux standard base ...  |     Infos über die Distribution ausgeben  
**uptime**   |    how long the system ...  |     Seit wann läuft das System und ...  
**dpkg**  |       debian package    |            Paketverwaltung für Debian  
**top**  |    display linux processes     |      Linux Prozesse anzeigen (Ende mit Taste q)  
**ps** |      process status |                Prozessdetails anzeigen  
**jobs**  |     show user processes   |        Eigene Prozesse anzeigen  
**kill**   |      kill/signal process  |         Signal an Prozess senden, Prozess beenden   
**free**   |      display free/used memory |     Arbeitsspeicher (RAM) anzeigen   
  
### Kommandos für die Benutzerverwaltung  
**Symbol** | **Englisch** | **Deutsch**
---------- | ---------- | ----------    
**whoami**  |     who am i    |               aktuellen Benutzer ausgeben  
**who**   |       who is logged on   |        wer ist gerade angemeldet  
**w**   |         who is logged on and ...   |  wer ist wie angemeldet  
**passwd**  |     set new password    |       Passwort neu setzen  
**su**   |        set (change) user id    |   andere Benutzer-ID annehmen  
**sudo**   |      super-user do   |           in den Super-User Mode (root) wechseln  
**login**  |      login with new session |    startet eine neue Session im System  
**id**   |        display user id ...   |     Benutzerinfos anzeigen  
**groups**  |     display groups |            Gruppenmitgliedschaft anzeigen  
**adduser**  |    add new user     |          Neuen Benutzer hinzufügen  
**deluser**  |    delete user     |           Benutzer entfernen  
  
### Kommandos für die Paketverwaltung  
**Symbol** | **Englisch** | **Deutsch**
---------- | ---------- | ----------    
**apt-get**   |    get data from repository  | Daten/Files herunterladen  
**dpkg**     |     debian package       |      Pakete installiern/deinstallieren  
**apt-cache**  |   packet cache commands   |   Kommandos für lokalen APT cache am Rechner  
  
Quelle: [LMS](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/7BF1B31508DF3.symlink?resource_id=0-385942208&m=view#154334970)  
  
---------------------------------
## Berechtigungen
Symbol | Englisch | Deutsch
---------- | ----------- | ------------
**r** | read | lesen
**w** | write | schreiben
**x** | execute | ausführen
**u** | user | Benutzer
**g** | group | Gruppe
**o** | others | Andere
#### Beispiel:
    rwx r-x r-x
* Der Benutzer darf lesen, schreiben und ausführen.
* Die Gruppe darf nur lesen und ausführen.
* Alle Anderen dürfen nur lesen und ausführen.
----------------------------------
## Neuen Benutzer erstellen
1) **Zum Superuser wechseln**
    
        sudo -i   
1) **"passwd" Datei bearbeiten**
    
        nano /etc/passwd/
1) **Passwort eingeben**
    
        sudo passwd name
1) **Erstellen des Home-Verzeichnis**
    
        mkdir/home/name
1) **Besitzer de Home-Verzeichnisses ändern**
    
        chown name /home/name
1) **Group Datei bearbeiten**
    
        nano /etc/group
1) **Gruppe des Benutzers wechseln**
    
        chgrp name /home/name
1) **"shadow" Datei bearbeiten**
    
        nano /etc/shadow
