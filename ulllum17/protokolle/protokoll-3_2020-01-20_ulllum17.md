# 3. Protokoll | AHME17
# Uller Lucas
--------------------------------------------------------------------------
* **Thema:** Raspberry PI
* **Datum:** 20.01.2020
* **Gefehlt:** Richard Strohriegel
* **Erstellt von:** ulllum17
* **Protokoll letzte Einheit:** [2.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/ulllum17/ulllum17/protokolle/protokoll_2019-10-14_ulllum17.md) 
* **Protokoll nächste Einheit:**
--------------------------------------------------------------------------
# Inhaltsverzeichnis

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
unzip-p Downloads/NamederZipDatei.zip | dd bs=4M of=/dev/nmcblk0
````
2. Unter Windows wird zusätzlich ein Tool benötigt. Den Windows benötigt ein Dateisystem. Abhilfe schafft das kostenlose Programm [Rufus](https://rufus.ie/).
1. Secure Shell aktivieren   
Wenn keine Möglichkeit hat, den Raspberry Pi per Tastatur, Maus und Bildschirm in Betrieb zunehmen, dann kann man auf der SD-Speicherkarte in der Boot-Partition eine leere Datei mit dem Namen "ssh" erstellen. Wenn man das mit Windows macht, dann muss man darauf achten, dass keine Dateiendung hinzugefügt wird.
Wenn Raspbian gestartet wird, dann wird SSH aktiviert und die Datei automatisch gelöscht.

### Installation Schematisch gezeigt

![RaspberrySchematisch](https://user-images.githubusercontent.com/55395678/73013794-4753cc00-3e19-11ea-9a84-21c90a1883c3.png)

### SSH
>Secure Shell oder SSH bezeichnet sowohl ein Netzwerkprotokoll als auch entsprechende Programme, mit deren Hilfe man auf eine sichere Art und Weise eine verschlüsselte Netzwerkverbindung mit einem entfernten Gerät herstellen kann. Häufig wird diese Methode verwendet, um lokal eine entfernte Kommandozeile verfügbar zu machen, das heißt, auf einer lokalen Konsole werden die Ausgaben der entfernten Konsole ausgegeben und die lokalen Tastatureingaben werden an den entfernten Rechner gesendet. Genutzt werden kann dies beispielsweise zur Fernwartung eines in einem entfernten Rechenzentrum stehenden Servers.  

Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Secure_Shell)

#### Warum ist die SSH standardmäßig deaktiviert? 
Früher war die Secure Shell standardmäßig aktiviert, aber da der Standardbenutzer und das Standardpasswort auf jedem PI gleich ist und ein *Laie* möglicher weiße kein neues Passwort festlegt bzw. keinen neuen Benutzer anlegt, somit kann eine fremde Person einfach auf den PI zugreifen.

//ToDo einstellungen etc.

## Man in the Middle
