# Protokoll m17-3ahme-la1

-----

**Name**: Andreas Augustin  
**Datum**: 11.11.2019  
**Klasse**: 3AHME  
**Gruppe**: 1  

-----

## Inhaltsverzeichniss

1) [Shell](#shell)
1) [SSH](#ssh)  
1) [Befehle](#befehle)  
    * [Features](#features) 
1) [Tastenkombinationen](#tastenkombinationen) 
1) [Rechte](#rechte)
1) [Neuer Benutzer](#neuer-benutzer)

-----

## Shell

Weil die direkte Kommunikation mit dem Betriebssystem-Kern für einen Benutzer viel zu komplex wäre, ist eine vereinfachte Benutzer-Schnittstelle erforderlich. Neben einer grafischen Schnittstelle wie dem X Window System wird diese Leistung vor allem von einer Shell bereitgestellt. Der englische Ausdruck Shell, zu Deutsch etwa Schale oder Ummantelung, drückt diesen Sachverhalt bereits aus. Die Übersetzung oder Symbolisierung als Muschel hat dabei wohl mehr mit Spieltrieb und Anschaulichkeit als mit einem echten technischen Hintergrund zu tun. Jedenfalls lässt sich eine Shell als eine Schicht zwischen Betriebssystem und Benutzer verstehen.

![](https://www.selflinux.org/selflinux/bilder/was_ist_shell_shell_funktionsweise01.png)

Quelle: [Selflinux](https://www.selflinux.org/selflinux/html/was_ist_shell01.html)

-----

## SSH

Secure Shell oder SSH bezeichnet sowohl ein Netzwerkprotokoll als auch entsprechende Programme, mit deren Hilfe man auf eine sichere Art und Weise eine verschlüsselte Netzwerkverbindung mit einem entfernten Gerät herstellen kann. Häufig wird diese Methode verwendet, um lokal eine entfernte Kommandozeile verfügbar zu machen, das heißt, auf einer lokalen Konsole werden die Ausgaben der entfernten Konsole ausgegeben und die lokalen Tastatureingaben werden an den entfernten Rechner gesendet. Genutzt werden kann dies beispielsweise zur Fernwartung eines in einem entfernten Rechenzentrum stehenden Servers. Die neuere Protokoll-Version SSH-2 bietet weitere Funktionen wie Datenübertragung per SFTP. 

Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Secure_Shell)

-----

## Befehle

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
    
  
### Features

 **Autovervollständigung**  
    Durch Tippen der Tabulatortaste. Vorschläge können durch zweimaliges Tippen der Tabulatortaste angezeigt werden.
    
 **In früheren Kommandos blättern (History)**
    Mit den Pfeiltasten ⇧ und ⇩
    
 **Cursor bewegen**
    Mit den Pfeiltasten ⇦ und ⇨ horizontal bewegen.
    Den Cursor zum Anfang (Pos1 oder Strg+a) oder Ende (Ende oder Strg+e) der Zeile bewegen
    
Quelle: [LMS](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/7BF1B31508DF3.symlink?resource_id=0-385942208&m=view#150960483)

-----

## Tastenkombinationen

    • Strg + Shift + c ... Kopieren in Zwischenablage  
    • Strg + Shift + v ... Einfügen aus Zwischenablage  
    • Strg + r ... Suchen nach früheren Kommandos  
    • Strg + l ... Löschen des Bildschirms  
    • Strg + c ... Abbrechen eines Kommandos  
    • Strg + z ... Pausieren eines Kommandos  
    • Strg + d ... Shell beenden (detach)  
    • Strg + t ... Die Zeichen unter dem Cursor tauschen  
    
## Rechte

Jeder Benutzer (owner,group,others) haben bestimmte Rechte. Diese Bestimmen was die Benutzer dürfen.

* r...read          man darf Dateien lesen
* w...write         man hat Schreibrechte für die Datei
* x...execute       man darf diese Datei ausführen

![](https://www.comentum.com/images/permissions.jpg)

## Neuer Benutzer

1) **Zum Superuser wechseln**                  sudo -i
1) **passwd Datei bearbeiten**                 nano /etc/passwd/
1) **Passwort eingeben**                       sudo passwd name
1) **Erstellen des Hom" Verzeichnis**          mkdir/home/name
1) **Besitzer vom Home Verzeichnis ändern**    chown name /home/name
1) **Group Datei Bearbeiten**                  nano /etc/group
1) **Gruppe des Benutzer's wechseln**          chgrp name /home/name
1) **shadow datei bearbeiten**                 nano /etc/shadow
