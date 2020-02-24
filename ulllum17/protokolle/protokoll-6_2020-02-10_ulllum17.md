# 6. Protokoll | AHME17 
# Uller Lucas
-------------------------------------------------------------------------
* **Thema:** Raspberry PI, SSH-Verbindungen
* **Datum:** 10.02.2020
* **Gefehlt:** Richard Strohriegel, Kilian Wade
* **Erstellt von:** ulllum17
* **Protokoll letzte Einheit:** [5.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/ulllum17/ulllum17/protokolle/protokoll-5_2020-02-03_ulllum17.md)
--------------------------------------------------------------------------
## Inhaltsverzeichnis

1. [APT](#apt)   
   1. [APT Befehle](#apt-befehle)   
1. [Netzwerk-Technik](#netzwerk-technik)
   1. [Bedeutung vom LOOPBACK](#bedeutung-vom-loopback)
   1. [Arten von Netzwerkstatus](#arten-von-netzwerkstatus)
1. [Netzwerk-Protokolle](#netzwerk-protokolle)
1. [Zwei Raspberry verbinden](#zwei-raspberry-verbinden)
   1. [Ping](#ping)
   1. [Internet Control Message Protocol (ICMP)](#internet-control-message-protocol-icmp)
   1. [Schnittstellen ein-/ausschalten](#schnittstellen-ein-ausschalten)
   1. [Address Resolution Protocol (ARP)](#address-resolution-protocol-arp)
   1. [IP-Addresse Statisch vergeben](#ip-addresse-statisch-vergeben)




--------------------------------------------------------------------------

## APT

> APT ist ein Paketmanagement-System, das im Bereich des Betriebssystems Debian GNU/Linux entstanden ist. Mittels APT ist es sehr einfach, Programmpakete zu suchen, zu installieren oder auch das ganze System auf den neuesten Stand zu bringen.

Quelle: [Ubuntuusers](https://wiki.ubuntuusers.de/APT/)

### APT Befehle

Mit folgendem Befehl werden die Paketlisten neueingelesen
````bash
apt update
````

Mit folgendem Befehl wird PAKETNAME installiert
````bash
apt install PAKETNAME
````

Mit folgendem Befehl wird die Paketliste angezeigt

````bash
apt list --upgradeable
````

Mit folgendem Befehl werden Installierte Pakete, wenn möglich, auf eine verbesserte Version aktualisiert. Um geänderte Abhängigkeiten zu erfüllen, werden gegebenfalls auch neue Pakete installiert.

````bash
apt upgrade
````
--------------------------------------------------------------------------
## Netzwerk-Technik

> Ein Computer Netzwerk ist eine Verbund zwischen mehreren Computern (mindestens zwei), die Daten gegeneinander austauschen. Die PCs können praktisch miteinander kommunizieren. Ein Computer Netzwerk hat aber nicht nur den Vorteil das Daten gegeneinander ausgetauscht werden können, sondern auch, dass auf man den gleichen Internetzugang verwendet oder auch einen gemeinsamen Drucker verwendet.

Quelle: [DeinElektriker](https://dein-elektriker-info.de/was-ist-ein-netzwerk/)

Die IP-Adresse kann mit folgendem Befehl abgefrag werden

````bash
ip addr show
````
oder die kurzversion
````bash
ip a
````

Die Ausgabe sieht kann dann wie folgt aussehen

````bash
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever

       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 08:00:27:66:72:e1 brd ff:ff:ff:ff:ff:ff
    inet 10.1.102.59/24 brd 10.1.102.255 scope global eth0
    inet6 fe80::a00:27ff:fe66:72e1/64 scope link 
       valid_lft forever preferred_lft forever
````

### Bedeutung vom LOOPBACK

Das Internet Protocol (IP) spezifiziert ein Loopback-Netzwerk. Speziell reservierte IP-Adressen sind für IPv4 der Adressraum von 127.0.0.1 bis 127.255.255.254[1], wobei meist 127.0.0.1 genutzt wird, und für IPv6 die Adresse ::1[2] Die meisten IP-Umsetzungen unterstützen eine Loopback-Schleife, wobei sämtliche Pakete, die ein Computerprogramm an diese Adressen sendet, an denselben Computer adressiert werden. Der Standard für Domains dieser Adressen ist localhost.

Auf Unix-ähnlichen Systemen wird die Loopback-Schnittstelle allgemein lo oder lo0 genannt.

Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Loopback)

### Arten von Netzwerkstatus

* up
* down
* unknown
--------------------------------------------------------------------------
## Netzwerk-Protokolle

* TCP-Protokoll
   * Portnummern vergabe, für die Programm zuordnung    
Mehr zu [TCP](https://de.wikipedia.org/wiki/Transmission_Control_Protocol) 

* Ethernet und Wlan Protokoll
   * Verinden von Computer, im Lokalen Netzwerk
   
* IP-Protokoll
   * Verbinden von Computer, im Internet    
   Mehr zu [IP](https://de.wikipedia.org/wiki/Internet_Protocol)
--------------------------------------------------------------------------
## Zwei Raspberry verbinden

In unserem Beispiel haben wir die Raspberry über das Ethernet verbunden und ein Subnetz erzeugt.

Um zu sehen ob die Schnittstelle funktioniert geben wir folgenden Befehl ein.

````bash
ip a
````

Die Ausgabe kann dann wie folgt aussehen
````bash
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqeue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BRODCAST, MULTICAST> mtu 1500 qdisc noop state UP qlen 1000
    link/ether 00:08:9b:c4:30:31 brd ff:ff:ff:ff:ff:ff 
3: eth1 <BRODCAST, MULITCAST, UP, LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:08:9b:c4:30:31 brd ff:ff:ff:ff:ff:ff
    inet 169.254.0.0/16 brd 169.254.42.199 scope global eth1
    inet6 fe80::208:9bff:fec4:3030/64 scope link
       valid_lft forever preferred_lft forever
````

Uns interessiert die Schnittstelle eth1, denn mit dieser Schnittstelle ist der PI verbunden.

Die **IP-Adresse** ist **169.254.42.199**

Zeroconf oder Zero Configuration Networking ist ein Vorhaben für die selbständige Konfiguration von Rechnernetzen ohne Eingriffe durch Menschen.    
Wenn ein Rechner eine Link-Local-IP-Adresse konfigurieren will, wählt er eine zufällige IP-Adresse zwischen 169.254.1.0 und 169.254.254.255 aus. Bei der Erzeugung der IP-Adresse sollte eine rechnerspezifische Information einfließen, wie etwa die MAC-Adresse der Netzwerkschnittstelle, damit möglichst jedes Mal dieselbe IP-Adresse generiert wird (sie wird also nur pseudozufällig gewählt).

### Ping

> Ping ist ein Diagnose-Werkzeug, mit dem überprüft werden kann, ob ein bestimmter Host in einem IP-Netzwerk erreichbar ist. Daneben geben die meisten heutigen Implementierungen dieses Werkzeuges auch die Zeitspanne zwischen dem Aussenden eines Paketes zu diesem Host und dem Empfangen eines daraufhin unmittelbar zurückgeschickten Antwortpaketes an (= Paketumlaufzeit, meist round trip time oder RTT genannt).

Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Ping_(Daten%C3%BCbertragung))

* Der Ping sendet sogenannte ICMP-Pakete.

Der Ping Befehl sieht wie folgt aus

````bash
ping <IP-Adresse>
````

### Internet Control Message Protocol (ICMP)

> Das Internet Control Message Protocol (ICMP) dient in Rechnernetzwerken dem Austausch von Informations- und Fehlermeldungen über das Internet-Protokoll in der Version 4 (IPv4). Für IPv6 existiert ein ähnliches Protokoll mit dem Namen ICMPv6.

Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Internet_Control_Message_Protocol)

Den ICMP Dienst sollte man nicht abschalten, denn die Router kommunizieren über dieses Protokoll.

### Schnittstellen ein-/ausschalten

Der Befehl dafür lautet

````bash
ip link set <Schnittstelle> <status>
````
* Für Schnittstelle kann Beispielsweise *eth0*, *eth1* eingesetzwerden   
* Für Status  *up* oder *down*

### Address Resolution Protocol (ARP)

> Das Address Resolution Protocol (ARP) ist ein Netzwerkprotokoll, das zu einer Netzwerkadresse der Internetschicht die physische Adresse (Hardwareadresse) der Netzzugangsschicht ermittelt und diese Zuordnung gegebenenfalls in den so genannten ARP-Tabellen der beteiligten Rechner hinterlegt.

Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Address_Resolution_Protocol)

Der Befehl dafür lautet 

````bash
ip n
````

### IP-Addresse Statisch vergeben

IP-Adresse vergeben

````bash
ip a s eth1
````

Beim IP-Adressen vergeben muss darauf geachtet werden das es öffentliche IPv4 und private IPv4 Adressen gibt.

|private|
|-------|
|10.0.0.0/8|
|172.16.0.0/12|
|192.168.0.0/16|

Wobei 8 | 12 | 16 die Netzmaske ist.

````bash
ip a add <IP-Adresse> dev <Schnittstelle>
````
