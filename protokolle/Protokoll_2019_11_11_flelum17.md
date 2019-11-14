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




## Kommandos  
* **Interne Kommandos**  
  Stellt die Shell selbst zur Verfügung  
  Hilfe: **help**  
  
* **Externe Kommandos**  
  Dort wirt ein externes Programm aufgerufen  
  Hilfe: **man**   
    
**Kommandos für Verzeichnisse und Dateien**  
pwd      print working directory   Aktuelles Arbeitsverzeichnis (.) ausgeben  
ls       list directory content    Dateien und Verzeichnisse von ./ ausgegeben  
cd       change directory          In ein (anderes) Verzeichnis wechseln  
touch    touch file                Leere Datei anlegen oder Zeitstempel ändern  
mkdir    make directory            Verzeichnis erstellen  
mv       move                      Datei/Verzeichnis verschieben oder umbenennen   
cp       copy                      Date/Verzeichnis kopieren  
scp      secure copy               copy über Netzwerk via ssh (secure shell)  
rm       remove                    Datei oder löschen  
rmdir    remove directory          Verzeichnis löschen (muss leer sein!)  
ln       link                      Links erstellen  
cat      concatenate               Dateien verbinden und auf stdout ausgeben  
less     less (is more)            Dateiinhalt im Viewer less anzeigen  
hexdump  hexadecimal file dump     Dateiinhalt als Hexdump ausgeben  
grep     global search for a       Auf ein Suchmuster passende Zeilen ausgeben
         regular expression and  
         print out matched lines    
find     find files                Dateien oder Verzeichnisse finden  
dd       duplicate data            Daten 1:1 kopieren (auch auf Geräte anwendbar)  
df       disk free space           Freien Speicher auf Dateisystemen anzeigen  
du       disk usage                Byte-Verbrauch in Verzeichnis(sen) zeigen  
mount    mount a filesystem        Partition einbinden  
umount   unmount a filesystem      Eingebundene Partition trennen
Bei Ubuntu kann anstelle des Kommandos find kann auch das Kommando   





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
[Shell](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/7BF1B31508DF3.symlink?resource_id=0-385942208&m=view#150960423) (12.11.2019)  




  
