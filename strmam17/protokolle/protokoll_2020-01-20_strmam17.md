# Protokoll Labor 3AHME (2020-01-20)
* Thema: Raspberry, Arduino, Rasperry einrichten
* Datum: 20.01.2020
* Gefehlt: Richard Strohrigl
* Erstellt von: strmam17
* Protokoll letzte Einheit: [Protokol 2019-10-14](https://github.com/HTLMechatronics/m17-3ahme-la1sx/blob/strmam17/strmam17/protokolle/protokoll_2019-10-14_strmam17.md)
* Protokoll nächste Einheit:
----------------------------------------------------------------------------------------------
## Inhaltsverzeichnis
1. [Arduino Nano und Raspberry Pi](#arduino-nano-und-raspberry-pi)
2. [Betriebssystem auf Raspberry](#betriebssystem-auf-raspberry)
      * [Über SSH auf das Gerät einsteigen](#über-ssh-auf-das-gerät-einsteigen)
      * [Überprüfen seines Gerätes](#überprüfen-seines-gerätes)
      * [Name und Passwort ändern](#name-und-passwort-ändern)
      * [Benutzer hinzufügen](#benutzer-hinzufügen)
      * [Benutzer deaktivieren](#benutzer-deaktivieren)
      * [Man in the middle](#man-in-the-middle)
----------------------------------------------------------------------------------------------
## Arduino Nano und Raspberry Pi

  Arduino Nano                            | Raspberry Pi
  ----------------------------------------|-----------------------------------------
  geringe Leistungsfähigkeit              | wesentlich Leistungsfähiger C>>1000
  einfachekostengünstige 8 Bit Architektur| sehr Leistungsfähige 32Bit Architektur
  Preis: 1-3€                             | Rasperry Zero: 12-14€; Raspberry Pi: 30€
  Kein Standartbetriebssystem möglich     | Standartbetriebssystem möglich
  0,022 kWh                               | 8,70 kWh
  Echtzeitfähig                           | nicht Echtzeitfähig
  Verschlüsselung nicht möglich           | Verschlüsselung möglich

[Echtzeitsystem](https://de.wikipedia.org/wiki/Echtzeitsystem): Es gibt eine Aufgabe mit einen Zeitschranken. Da das nicht immer zusammen passt muss er nachjustieren.

--------------------------------------------------------------------------------------------------
## Betriebssystem auf Raspberry
Wir nahmen das Betriebssystem Raspian Buster Lite. Da das aber eine ZIP-Datei ist braucht man ein tool um es zu Entzippen. Bei Windows muss man ein extra tool downloaden, bei Ubuntu nicht da es dort schon ein kommando dafür gibt, nähmlich dd:

    Unzip -p 2019-09.26-raspbian-buster-lite-zip |dd bs=4M of = /dev/mcblk0
    
Auf MMC-Karte speichern:
 
    mount /dev/mmcblk0p1
    touch /media/boot/ssh
    unmount /dev/mmcblk0p1
    
### Über SSH auf das Gerät einsteigen
Man braucht zum einsteigen auf das Gerät die IP-Adresse des Gerätes.

    sshpi@10.200.114.217
    Passwort: raspberry 
    
Beim ersten mal einloggen muss man beachten, dass die amerikanische Tastatur eingestellt ist also muss man anstatt y z eingeben.

### Überprüfen seines Gerätes
Man muss überprüfen ob man auf seinen eigenen Gerät eingeloggt ist.

    ip a
    
### Name und Passwort ändern
Seinen Namen kann man mit den folgenden Befehlen ändern.

    sudo nano /etc/hostname
    sudo nano /etc/hosts

Danach wieder aussteigen um das passwort zu ändern.

    sudo reboot
    
Passwort ändern mit:

    passwd
    
### Benutzer hinzufügen

    sudo adduser <Bentzer>
    
Kommando dafür, dass der neue Benutzer alle Rechte bekommt.

    pi@pi17 sudo usermod -G sudo <Benutzer>
    
### Benutzer deaktivieren
Man kann den alten Benutzer mit dem neuen Benutzer deaktiviern, aber nur wenn der neu Benutzer alle Rechte hat.

      passwd nologin
      
### Man in the middle

![MIA](http://wiki.cas.mcmaster.ca/images/3/38/Man_in_the_Middle.jpg)

Da der Login-Name und das passwort über das Netzwerk geht kann es sein, dass wir einen Hacker dazwischen haben also einen "Man in the middle". Also muss man überprüfen dass man keinen MIA dazwischen haben.

    schueler@pxx:ssh -keyscan 10.200.114.217
    
Dann muss man es mit seinem Gerät vergleichen.

    strmam17@pi17:ssh -keyscan pi17
    
Wenn man zu 100 prozent sicher sein will, dass es keinen MIA gibt muss man direkt zum Gerät gehen und dort arbeiten.


