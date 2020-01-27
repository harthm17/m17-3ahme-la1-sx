# 3. Protopkoll

------------------------------

* **Thema:** Raspberry, Arduino, Rasperry einrichten
* **Datum:** 20.01.2020
* **Gefehlt:** Strohtiegl
* **Gruppe:** 4
* **Protkollverfasser:** Uhl Julian
* **Letztes Protokoll:** [2. Protokol](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/uhljum17/uhljum17/protokolle/protkoll_2019-10-14_uhljum17.md)
* **Nächstes Protkoll:** [4. Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/uhljum17/uhljum17/%20protokolle/protkoll_2020-01-27_uhljum17.md)

------------------------------

# Inhaltsverzeichnis
  1. [Arduino Nano und Raspberry Pi](Arduino-Nano-und-Raspberry-Pi)
  2. [Betriebssysteme](Betriebssysteme)
      1. [SSH](SSH)
      2. [Über SSH auf das Netzwerk zugreifen](Über-SSH-auf-das-Netzwerk-zugreifen)
      
  3.[Man in the Middle](Man-in-the-Middle)
      

------------------------------
## Arduino Nano und Raspberry Pi

  Arduino Nano                                | Raspberry Pi
  --------------------------------------------|-----------------------------------------
  keine Verschlüsselung möglich               | Verschlüsselung möglich
  einfeche, kostengünstige 8Bit Architektur   | leistungsfähigere 32Bit Architektur
  Preis ca. 1-3€                              | Preis ca. 30€+
  kein Standartbetriebsystem                  | Standartbetriebssystem möglich (Respbian, Linux Debian)
  Verbrauch ca. 5mA (umgerechntet 4 Cent/Jahr)| Verbrauch ca. 1W (umgerechnet ca. 1-2€/Jahr)
  echtzeitfähig                               | nicht echtzeitfähig 
  
  Echtzeitfähig Bedeutet: es muss 100% gewährleistet sein, dass eine Aufgabe in z.B. in 1ms erledigt ist. (z.B. beim Röntegn)
  
  Das Pi in Raspberry steht für: Python (Programmiersprache)
  
         Linux 
           |
         Debian
       |       |
    Ubuntu ~ Raspbian
     (PC)     (RPI)
 
--------------------------------------

## Betriebssysteme

  In der Schule benutze wir Raspian Buster Lite, da das die minimalistische Version ist und wir mehr nicht brauchen. Die anderen beiden     Versionen sind auf der Website zu finden.
  
  Zum Endzippen wird bei Windows ein zusatzprogramm benötigt, bei Ubuntu gibt es dafür dd.

[Webseite von Raspberry](https://www.raspberrypi.org) 

[Zum Download](https://www.raspberrypi.org/downloads)

Auf den neusten Paspberries ist auch auch möglich Windows laufen zu lassen.

### SSH

>Secure Shell oder SSH bezeichnet sowohl ein Netzwerkprotokoll als auch entsprechende Programme, mit deren Hilfe man auf eine sichere Art und Weise eine verschlüsselte Netzwerkverbindung mit einem entfernten Gerät herstellen kann. Häufig wird diese Methode verwendet, um lokal eine entfernte Kommandozeile verfügbar zu machen, das heißt, auf einer lokalen Konsole werden die Ausgaben der entfernten Konsole ausgegeben und die lokalen Tastatureingaben werden an den entfernten Rechner gesendet. Genutzt werden kann dies beispielsweise zur Fernwartung eines in einem entfernten Rechenzentrum stehenden Servers. Die neuere Protokoll-Version SSH-2 bietet weitere Funktionen wie Datenübertragung per SFTP. 

Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Secure_Shell)

#### Über SSH auf das Netzwerk zugreifen
 
 Datei anlegen
   
    touch /media/boot/ssh
    
    unmount /dev/mmcblk0p1
    
    unmount /dev/mmcblk0p2
    

**Name und Passwort ändern**

Um Namen und passwort zu ändern folgendes machen:

    sudo nano /etc/hostname

    sudo nano /etc/hosts

    sudo reboot
    
Passwort ändern mit:

     passwd

Danach einfach neuen Namen und Passwort eingeben.

mit `ip a` kann man überpfüfen ob man man auf seinem Gerät ist(Ip-Adresse)


**Bemutzer hinzufügen**

    add user<Benutzer>
    
 falls man den Benutzer Rechte geben will
 
    sudo usermod -G sudo <Benutzer>

**Benutzer deaktivieren**

falls man alle rechte kann man den anderen Benutzer deaktivieren

    passwd nologin

-----------------------------

## Man in the Middle

>Ein Man-in-the-Middle-Angriff (MITM-Angriff), auch Janusangriff (nach dem doppelgesichtigen Janus der römischen Mythologie) genannt,    ist eine Angriffsform, die in Rechnernetzen ihre Anwendung findet. Der Angreifer steht dabei entweder physisch oder – heute meist –   logisch zwischen den beiden Kommunikationspartnern, hat dabei mit seinem System vollständige Kontrolle über den Datenverkehr zwischen zwei oder mehreren Netzwerkteilnehmern und kann die Informationen nach Belieben einsehen und sogar manipulieren. Die Janusköpfigkeit des Angreifers besteht darin, dass er den Kommunikationspartnern vortäuscht, das jeweilige Gegenüber zu sein. 


  ![MIA](http://wiki.cas.mcmaster.ca/images/3/38/Man_in_the_Middle.jpg)

Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Man-in-the-Middle-Angriff)

Der Man in the Middle könnte bei uns den Nutzernamen und das Passwort bekommen.

Um die Schlüssel zu vergelichen muss man

       schueler@pxx: ssh-keysan 10.200.114.227
       
       uhljum17@pi27: ssh-keyscan pi17
       
       
eingeben.
