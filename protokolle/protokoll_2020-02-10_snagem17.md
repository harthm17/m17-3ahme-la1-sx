# Protokoll Labor/SX 3AHME (2019/20)

* **Thema:** Raspberry über Netzwerk verbinden
* **Datum:** 10.02.2020
* **Gefehlt:** Kilian Wade, Richard Strohriegl
* **Erstellt von:** Georg Schnabel                 
* **Protokoll letzte Einheit:** [5.Protokoll](protokoll_2020-02-03_snagem17.md)

## Inhaltsverzeichnis

1. [Programme installieren](#programme-installieren)
   1. [rsync](https://wiki.ubuntuusers.de/rsync/)
1. [Alternativen zu rsync](#alternativen-zu-rsync)
   1. [APT](https://de.wikipedia.org/wiki/Advanced_Packaging_Tool)     
   1. [tcpdump](https://wiki.ubuntuusers.de/tcpdump/)      
1. [Raspberry über Netzwerk verbinden](#raspberry-über-netzwerk-verbinden)
   1. [Netzwerkprotokolle](https://de.wikipedia.org/wiki/Netzwerkprotokoll)
   1. [Loopback](https://de.wikipedia.org/wiki/Loopback)
   1. [ICMP-Protokoll](https://de.wikipedia.org/wiki/Internet_Control_Message_Protocol)
   1. [Private IP-Adressen](https://de.wikipedia.org/wiki/Private_IP-Adresse)
   1. [Ping](https://de.wikipedia.org/wiki/Ping_(Datenübertragung))
1. [Verbinden mit dem Partner](#verbinden-mit-dem-anderen-raspberry)
  
 ## Programme installieren
 ### rsync
 Quelle: [ubuntuusers](https://wiki.ubuntuusers.de/rsync/)
> rsync ist ein Programm, um Dateien zwischen lokalen oder über das Netzwerk erreichbaren Pfaden abzugleichen. Dabei werden zunächst die Größe und die Änderungszeit der Dateien in Quelle und Ziel verglichen, so dass nur die Dateien behandelt werden müssen, bei denen es Änderungen gegeben hat.
 
## Alternativen zu rsync
### APT
Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Advanced_Packaging_Tool)
> Das Advanced Packaging Tool (APT) ist ein Paketverwaltungssystem, das im Bereich des Betriebssystems Debian entstanden ist und dpkg zur eigentlichen Paketverwaltung benutzt. Ziel ist es, eine einfache Möglichkeit zur Suche, Installation und Aktualisierung von Programmpaketen zur Verfügung zu stellen.

#### Befehle von APT
**Pakete neu einlesen**
```
apt update
```
**Paketname installieren**
```
apt install PAKETNAME
```
**Paketliste anzeigen**
```
apt list --upgradeable
```

### tcpdump

[tcpdump](https://wiki.ubuntuusers.de/tcpdump/)

TCP-Dump ist ein Kommandozeilenprogramm. Damit kann man kontrollieren welche Pakete ankommen und weggeschickt werden.
```
apt-get install tcpdump
```

  ## Raspberry über Netzwerk verbinden
  
  ### Netzwerkprotokolle
  Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Netzwerkprotokoll)
  > Ein Netzwerkprotokoll ist ein Kommunikationsprotokoll für den Austausch von Daten zwischen Computern bzw. Prozessen, die in einem Rechnernetz miteinander verbunden sind. Die Vereinbarung besteht aus einem Satz von Regeln und Formaten, die das Kommunikationsverhalten der kommunizierenden Instanzen in den Computern bestimmen. 
  
  * Das [TCP-Protokoll](https://de.wikipedia.org/wiki/Transmission_Control_Protocol) wird häufig verwendet. Es sorgt dafür, dass Programme Daten miteinander austauschen können und diese in richtiger Reihenfolge und fehlerfrei ankommen. 
  * Das [IP-Protokoll](https://de.wikipedia.org/wiki/Internet_Protocol) ermöglicht das Verbinden von Computern weltweit.(IPv4, IPv6)
  * Das [Ethernet/WLAN-Protokoll](https://de.wikipedia.org/wiki/Ethernet) ermöglicht die Verbindung von Computern in einem Netzwerk in unmittelbarer Nähe.
  
   ### Private IP-Adressen
 Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Private_IP-Adresse)
 > Private IP-Adressen (abgekürzt Private IP) sind IP-Adressen, die von der IANA nicht im Internet vergeben sind. Sie wurden für die private Nutzung aus dem öffentlichen Adressraum ausgespart. Als die IP-Adressen des Internet Protokolls v4 knapp wurden und dadurch eine bewusste Einsparung öffentlicher IP-Adressen notwendig wurde, war es umso wichtiger, private IP-Adressen in lokalen Netzwerken zur Verfügung zu haben, die beliebig oft bzw. in beliebigen Netzwerken genutzt werden können.
  
  ### Loopback
  Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Loopback)
  > Ein Loopback oder eine Schleifenschaltung ist ein Nachrichten- oder Informationskanal mit nur einem Endpunkt, so dass Sender und Empfänger identisch sind. 
In der Kommunikationstechnologie werden Loopbacks gewöhnlich benutzt, um die Erreichbarkeit eines Ziels zu prüfen.

### ICMP-Protokoll

Quelle:[Wikipedia](https://de.wikipedia.org/wiki/Internet_Control_Message_Protocol)
> Das Internet Control Message Protocol (ICMP) dient in Rechnernetzwerken dem Austausch von Informations- und Fehlermeldungen über das Internet-Protokoll in der Version 4 (IPv4). Für IPv6 existiert ein ähnliches Protokoll mit dem Namen ICMPv6. 

Diesen Dienst sollte man nicht abschalten, da der Router über dieses Protokoll kommuniziert.

 ### Ping
 Der **ping** Befehl ist ein Tool, mit dem man überprüfen kann, ob ein Host in einem IP-Netzwerk erreichbar ist. Der Teilnehmer, der es überprüfen will,  versendet ein ICMP-Pakete an den anderen Netzwerkteilnehmer (er pingt ihn an). Der angepingte Teilnehmer beantwortet diese Anfrage und somit ist die Frage der Erreichbarkeit geklärkt.
 
 **Ping-Befehl:**
 ```
 ping <IP-Adresse
 ```
 
 ## Verbinden mit dem anderen Raspberry
 Wir mussten die Raspberrys mit Ethernet verbinden, dadurch haben wir ein Subnetz erzeugt. Mit dem Kommando **ip addr show** konnten wir die aktuellen Schnittstellen mit den dazugehörigen IP-Adressen sehen. Es gibt auch eine Kurzversion die einfach **ip a** lautet.
 ```
 ip addr show
 ```
 ```
 ip a
 ```
 
 Schaut folgendermaßen aus:
  ```bash
 pi@pi24-GL752VW:~$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 70:8b:cd:24:5b:de brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether b8:8a:60:64:a7:35 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.5/24 brd 10.0.0.255 scope global dynamic noprefixroute wlp2s0
       valid_lft 83229sec preferred_lft 83229sec
    inet6 fe80::bf71:d65:3007:b4ab/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
```
Mit der Schnittstelle **eth1** ist unser Raspberry verbunden.
