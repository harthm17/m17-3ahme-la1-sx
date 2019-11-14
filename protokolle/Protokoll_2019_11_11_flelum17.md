# Labor- Protokoll 2019-11-11  

**Lukas Fleischhacker**  
**3AHME**  

-----------------------------  

## Inhaltsverzeichnis  
   * [Shell](#shell)  
   * [SSH](#ssh)  
   * [Kommandos](#kommandos)  
   * [Features](#features)  
   * [Rechte](#rechte)    
   * [Benutzer](#benutzer)  
   * [Quellen](#quellen)  

-----------------------------  

## Shell  
**Eingabekonsole**  
Steuerung/Konfiguration des Systems mit textuellen Kommandos  
    
* *Effizienteres Arbeiten*  
* *Befehle und Befehlsketten sind leicht dokumentierbar*  
* *Auch bei Fernwartung über schlechte Netzwerkverbindung verwendbar*  
* *Keine intuitive Arbeitsweise*  
* *Erfordert eine gründliche Schulung*  





## SSH  
  **Secure Shell** oder **SSH** bezeichnet sowohl ein *Netzwerkprotokoll* als auch entsprechende *Programme*,  
  mit deren Hilfe man auf eine sichere Art und Weise eine *verschlüsselte Netzwerkverbindung* mit   
  einem entfernten Gerät herstellen kann. Häufig wird diese Methode verwendet, um lokal eine   
  entfernte Kommandozeile verfügbar zu machen, das heißt, auf einer lokalen Konsole werden die  
  Ausgaben der entfernten Konsole ausgegeben und die lokalen Tastatureingaben werden an den   
  entfernten Rechner gesendet. Genutzt werden kann dies beispielsweise zur *Fernwartung* eines  
  in einem entfernten Rechenzentrum stehenden Servers.  



## Kommandos  
* **Interne Kommandos**  
  Stellt die Shell selbst zur Verfügung  
  Hilfe: **help**  
  
* **Externe Kommandos**  
  Dort wirt ein externes Programm aufgerufen  
  Hilfe: **man**   
    
### Kommandos für Verzeichnisse und Dateien  

**Befehl** | **Bedeutung** | **Erklärung**
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
  
**+** global search for a regular expression and print out matched lines   


### Kommandos für Betriebssystem und Prozesse  

**Befehl** | **Bedeutung** | **Erklärung**
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

**Befehl** | **Bedeutung** | **Erklärung**
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

**Befehl** | **Bedeutung** | **Erklärung**
---------- | ---------- | ----------    
**apt-get**   |    get data from repository  | Daten/Files herunterladen  
**dpkg**     |     debian package       |      Pakete installiern/deinstallieren  
**apt-cache**  |   packet cache commands   |   Kommandos für lokalen APT cache am Rechner  

  
  


## Features  
* **Autovervollstänigung** Tabulatortaste  
* **History** Pfeiltasten auf und ab  
* **Cursor** Pfeiltasten links und rechts  
* **Tastenkombinationen**  
  
             Strg + Shift + c ... Kopieren in Zwischenablage  
             Strg + Shift + v ... Einfügen aus Zwischenablage  
             Strg + r ........... Suchen nach früheren Kommandos  
             Strg + l ........... Löschen des Bildschirms  
             Strg + c ........... Abbrechen eines Kommandos  
             Strg + z ........... Pausieren eines Kommandos  
             Strg + d ........... Shell beenden  
             Strg + t ........... Die Zeichen unter dem Cursor tauschen  


* **Verkettung von Kommandos** mit |  
* **Mehrere Kommandos in der Zeile** mit ;  


## Rechte  




## Benutzer  

## Quellen  
[LMS(Shell)](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/7BF1B31508DF3.symlink?resource_id=0-385942208&m=view#150960423) (14.11.2019)  
[Wikipedia(SSH)](https://de.wikipedia.org/wiki/Secure_Shell) (14.11.2019)  




  
