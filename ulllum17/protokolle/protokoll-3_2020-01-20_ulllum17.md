# 3. Protokoll | AHME17
# Uller Lucas
--------------------------------------------------------------------------
* **Thema:** Raspberry PI
* **Datum:** 20.01.2020
* **Gefehlt:** Richard Strohriegel
* **Erstellt von:** ulllum17
* **Protokoll letzte Einheit:** [2.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/ulllum17/ulllum17/protokolle/protokoll-2_2019-10-14_ulllum17.md) 
* **Protokoll nächste Einheit:**
--------------------------------------------------------------------------
# Inhaltsverzeichnis
1. [Vergleich Arduino Nano und Raspberry](#vergleich-arduino-nano-und-raspberry)    
1. [Betriebssysteme](#betriebssysteme)    
   1. [Installation + SSH Aktivierung](#installation--ssh-aktivierung)    
1. [SSH](#ssh)    
   1. [Warum ist die SSH standardmäßig deaktiviert?](#warum-ist-die-ssh-standardmäßig-deaktiviert)   
1. [Auf den PI zugreifen](#auf-den-pi-zugreifen)   
1. [Man in the Middle](#man-in-the-middle)    
   1. [Abhilfe](#abhilfe)   

--------------------------------------------------------------------------

# Vergleich Arduino Nano und Raspberry

|     | **Arduino Nano** | **Raspberry PI** | 
|:-----:|:--------------:|:--------------:|
| **CPU** |geringe Leistungsfähigkeit| wesentlich leistungsfähiger (Faktor 1000)|
|**Architektur**|8-Bit|32-Bit|
|**Preis**| 1-3€                     |  12-14€ (Zero) , 30€ (voller PI)|
|**Betriebssystem**| kein Standard Betriebssystem| Standard Betriebssystem möglich|
| | |- Raspian(Linux, Debian)|
|**Leistung**|~2,5mW|~1W|
|**Echtzeitfähig**|JA|NEIN|

## Echtzeitfähig 
>Als Echtzeitsysteme (englisch real-time systems) werden „Systeme zur unmittelbaren Steuerung und Abwicklung von Prozessen“ bezeichnet, die dafür an sie gestellte quantitative Echtzeitanforderungen erfüllen müssen. Diese kommen in diversen Technikgebieten zur Anwendung, etwa in der Prozessleittechnik, in Motorsteuerungen, in der Satellitensystemtechnik, in Signal- und Weichenstellanlagen, in der Robotik und in weiteren Bereichen.

Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Echtzeitsystem)

--------------------------------------------------------------------------
# Betriebssysteme

Die Betriebssysteme können auf der offiziellen Seite von Raspberry Pi heruntergeladen werden.   
[Raspberry PI Downloads](https://raspberrypi.org/downloads)

Wir haben uns für das Raspian entschieden. Dabei handelt es sich um eine Debian Distributation, welche für die ARM-Architektur des Raspberry PIs in den vergangen Jahren optimiert und verschlankt wurde.

## Installation + SSH Aktivierung

1. Betriebssystem als ZIP-Datei Download
1. Unter Linux wird das Betriebssystem wie folgt auf die MMC kopiert

````bash
unzip-p 2019-09.26-raspbian-buster-lite-zip | dd bs=4M of=/dev/nmcblk0
````
2. Unter Windows wird zusätzlich ein Tool benötigt. Den Windows benötigt ein Dateisystem. Abhilfe schafft das kostenlose Programm [Rufus](https://rufus.ie/).
1. Secure Shell aktivieren   
Wer keine Möglichkeit hat, den Raspberry Pi per Tastatur, Maus und Bildschirm in Betrieb zunehmen, dann kann man auf der SD-Speicherkarte in der Boot-Partition eine leere Datei mit dem Namen "ssh" erstellen. Wenn man das mit Windows macht, dann muss man darauf achten, dass keine Dateiendung hinzugefügt wird.
Wenn Raspbian gestartet wird, dann wird SSH aktiviert und die Datei automatisch gelöscht.

### Installation Schematisch gezeigt

![RaspberrySchematisch](https://user-images.githubusercontent.com/55395678/73013794-4753cc00-3e19-11ea-9a84-21c90a1883c3.png)

### SSH
>Secure Shell oder SSH bezeichnet sowohl ein Netzwerkprotokoll als auch entsprechende Programme, mit deren Hilfe man auf eine sichere Art und Weise eine verschlüsselte Netzwerkverbindung mit einem entfernten Gerät herstellen kann. Häufig wird diese Methode verwendet, um lokal eine entfernte Kommandozeile verfügbar zu machen, das heißt, auf einer lokalen Konsole werden die Ausgaben der entfernten Konsole ausgegeben und die lokalen Tastatureingaben werden an den entfernten Rechner gesendet. Genutzt werden kann dies beispielsweise zur Fernwartung eines in einem entfernten Rechenzentrum stehenden Servers.  

Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Secure_Shell)

#### Warum ist die SSH standardmäßig deaktiviert? 
Früher war die Secure Shell standardmäßig aktiviert, aber da der Standardbenutzername und das Standardpasswort auf jedem PI gleich ist und ein *Laie* möglicher weiße keine Passwort änderung macht bzw. keinen neuen Benutzer anlegt, kann eine fremde Person einfach auf den PI zugreifen.

### Auf den PI zugreifen

Da wir die SSH aktiviert haben können wir mithilfe der Shell von Linux auf den PI zugreifen. Mit der Windows CMD geht das nicht. Hier für wird wieder ein Zusatzprogamm benötig, wie zum Beispiel [Putty](https://www.putty.org/)

Jeder PI hat bei uns eine feste IP-Adresse zugewiesen bekommen.   
IP-Adresse: 10.200.114.226
````bash
ssh pi@10.200.114.226
````

#### Name des PIs ändern
````bash
sudo nano /etc/hostname
sudo nano /etc/hosts
````
In unserem Fall in **pi26**

#### Passwort änderung
````bash
passwd
````

#### PI Neustarten
````bash
sudo reboot
````

#### Benutzer hinzufügen

````bash
sudo adduser <Benutzer>
````
**Superuser vergeben**
````bash
pi@pi26 sudo usermod -G sudo <Benutzer>
````


## Man in the Middle

![Der Schädling klinkt sich als Man-in-the-Middle in verschlüsselte Verbindungen ein.](https://www.heise.de/security/imgs/07/2/4/5/6/8/3/2/fortnite-schaubild-bb26f320820ea282.png)
Quelle: [heise.de](https://www.heise.de/security/artikel/Man-in-the-Middle-Angriff-Online-Zocker-im-Visier-von-Online-Kriminellen-4101275.html)

>Ein Man-in-the-Middle-Angriff (MITM-Angriff), auch Janusangriff (nach dem doppelgesichtigen Janus der römischen Mythologie) genannt, ist eine Angriffsform, die in Rechnernetzen ihre Anwendung findet. Der Angreifer steht dabei entweder physisch oder – heute meist – logisch zwischen den beiden Kommunikationspartnern, hat dabei mit seinem System vollständige Kontrolle über den Datenverkehr zwischen zwei oder mehreren Netzwerkteilnehmern und kann die Informationen nach Belieben einsehen und sogar manipulieren. Die Janusköpfigkeit des Angreifers besteht darin, dass er den Kommunikationspartnern vortäuscht, das jeweilige Gegenüber zu sein.

Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Man-in-the-Middle-Angriff)

### Abhilfe

SSH (Secure Shell) bietet eine Möglichkeit, durch Fingerabdruck („fingerprint“) nach dem erstmaligen Anmelden („login“) zu prüfen, ob man tatsächlich den Zielrechner erreicht hat.

**Auslese der Hash Prüfung, am PI und am eigenen Gerät, wenn der Hash übereinstimmt ist die Verbindung "sicher".**

Der Hash zum PI
````bash
ssh -keyscan 10.200.114.217
````
Der Hash am PI
````bash
ssh -keyscan pi17
````



