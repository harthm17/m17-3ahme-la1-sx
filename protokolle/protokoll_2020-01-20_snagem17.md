# Protokoll Labor/SX 3AHME (2019/20)

* **Thema:** Raspberry Pie
* **Datum:** 20.01.2020
* **Gefehlt:** Strohriegl
* **Erstellt von:** Georg Schnabel
* **Protokoll letzte Einheit:** [protokoll_2019-10-14_snagem17.md](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/snagem17/protokolle/protokoll_2019-10-14_snagem17.md)
* **Protokoll nächste Einheit:**

## Inhaltsverzeichnis
1. [Raspberry Pi](https://de.wikipedia.org/wiki/Raspberry_Pi), [Arduino Nano](http://www.geeetech.com/wiki/index.php/Arduino_Nano)
  * Informationen über RPI
  * Informationen über Arduino Nano
2. Inbetriebnahme des [Raspberry Pi](https://de.wikipedia.org/wiki/Raspberry_Pi)
  * Installation
  * über SSH zugreifen
  * Veränderungen vornehmen


### Raspberry Pi und Arduino Nano
Ein [Raspberry Pie](https://de.wikipedia.org/wiki/Raspberry_Pi) ist ein vollwärtiger Computer.

>Der Raspberry Pi ist ein Einplatinencomputer, der von der britischen Raspberry Pi Foundation entwickelt wurde. Der Rechner enthält ein Ein-Chip-System (SoC) von Broadcom mit einer ARM-CPU. Die Platine hat das Format einer Kreditkarte.<
* Quelle : (https://de.wikipedia.org/wiki/Raspberry_Pi)

[Arduino Nano](http://www.geeetech.com/wiki/index.php/Arduino_Nano) ist eine kostengünstigere Variante, hat aber weniger zum bieten.

>Das Arduino Nano ist ein kleines, komplettes und breadboard-freundliches Board, das auf dem ATmega328 (Arduino Nano 3.0) oder ATmega168 (Arduino Nano 2.x) basiert. Es hat mehr oder weniger die gleiche Funktionalität wie die Arduino Duemilanove, aber in einem anderen Paket. Es fehlt nur eine DC-Netzbuchse und funktioniert mit einem Mini-B USB-Kabel anstelle eines Standard-Kabels. Der Nano wurde von Gravitech entwickelt und wird produziert.<
* Quelle: (http://www.geeetech.com/wiki/index.php/Arduino_Nano)

#### Informationen über RPI
1. Er ist sehr Leistungsfähig (32Bit Architektur)
2. Volle RPI kostet ca. 30 Euro
3. Auf einem RPI ist auch ein Standardbetriebssystem möglich (z.B. Linux Debian)
4. Wesentlich mehr Leistung als Arduino Nano (>>1000)
5. Benötigt auf das Jahr gerechnet 8,76kWh Leistung

![RPI](https://www.bing.com/images/search?view=detailV2&ccid=TzozUZg1&id=2A5A6FBD810A790BDD42FBD4DED3E0D48DA373F6&thid=OIP.TzozUZg14o5j1Z6qpG6J1AAAAA&mediaurl=https%3a%2f%2fupload.wikimedia.org%2fwikipedia%2fcommons%2fthumb%2f4%2f45%2fRaspberry_Pi_-_Model_A.jpg%2f220px-Raspberry_Pi_-_Model_A.jpg&exph=220&expw=220&q=raspberry+pi&simid=607999074534493926&selectedIndex=8&ajaxhist=0)



#### Informationen über Arduino Nano
1. Hat eine 8Bit Architektur
2. Der Preis liegt zwischen 1-3 Euro
3. Auf einem Arduino Nano ist kein Standardbetriebssystem möglich
4. Hat eine geringe Leistung
5. Benötigt auf das Jahr gerechnet 0,022kWh Leistung

### Inbetriebnahme des Raspberry Pies
#### Installation
1. Das gewünschte Betriebssystem als Zip-Datei downloaden.
2. Windows braucht ein zusätzliches Tool und ein Dateisystem. Linux braucht kein Zusatz Tool und die Zip-Datei kann direkt auf die MMC-Karte kopiert werden.
3. Über die Secure Shell auf das Netzwerk des RPIs zugreifen. Man sollte den Raspberry Pie über Bildschirm und Maus in Betrieb nehmen, weil man dann eine Datei mit dem Namen ssh anlegen kann.
**Wichtig:** Bei Windows darf man keine Dateieendung hinzufügen, da beim boot dann die Datei von der ssh gelöscht wird.

#### SSH
Wir wollen über die [SSH](https://de.wikipedia.org/wiki/Secure_Shell) auf das Netzwerk zugreifen. Früher war die SSH standardmäßig aktiviert, doch heutzutage ist das nicht mehr so, weil wenn man ein ungeeignetes Passwort hat, können andere auf dem Raspberry Pi zugreifen und Veränderungen vornehmen bzw. Schaden anrichten.

So legt man eine SSH an:
```
touch/media/Schnabel/boot/ssh
```
#### Veränderungen vornehmen

Der Grund warum man z.B. Name und Passwort ändert ist, weil es bei den Raspberrys gleich ist. Erst wenn amn das Login geändert hat, kann kein anderer mehr auf dem RPI zugreifen und man ist viel sicherer.

**Name ändern:**
```
sudo /nano/etc/hostname
```
**Passwort ändern:**
```
passwd
```
