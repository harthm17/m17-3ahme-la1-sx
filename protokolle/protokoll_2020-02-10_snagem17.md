# Protokoll Labor/SX 3AHME (2019/20)

* **Thema:** Raspberry über Netzwerk verbinden
* **Datum:** 10.02.2020
* **Gefehlt:** Kilian Wade, Richard Strohriegl
* **Erstellt von:** Georg Schnabel
* **Protokoll letzte Einheit:** [5.Protokoll](protokoll_2020-02-03_snagem17.md)

## Inhaltsverzeichnis
1. [Programme installieren](#programme-installieren)
  * Alternativen zu [rsync](https://de.wikipedia.org/wiki/Rsync)
2. [Raspberry über Netzwerk verbinden](#raspberry-über-netzwerk-verbinden)
  * [Netzwerkprotokolle](https://de.wikipedia.org/wiki/Netzwerkprotokoll)
  * [Loopback](https://de.wikipedia.org/wiki/Loopback)
  * [Private IP-Adressen](https://de.wikipedia.org/wiki/Private_IP-Adresse)
  * [Ping](https://de.wikipedia.org/wiki/Ping_(Datenübertragung))
3. [Verbinden mit dem Partner](#verbinden-mit-dem-partner)
  
 ## Programme installieren
 
 Damit man Programme installieren kann, wird häufig das Kommando **rsync** verwendet.
 
### Alternativen zu rsync
* [APT](https://de.wikipedia.org/wiki/Advanced_Packaging_Tool)

Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Advanced_Packaging_Tool)
>Das Advanced Packaging Tool (APT) ist ein Paketverwaltungssystem, das dpkg zur eigentlichen Paketverwaltung benutzt. Ziel ist es, eine einfache Möglichkeit zur Suche, Installation und Aktualisierung von Programmpaketen zur Verfügung zu stellen.

* [tcpdump](https://wiki.ubuntuusers.de/tcpdump/)

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
  
  ### Loopback
  Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Loopback)
  > Ein Loopback oder eine Schleifenschaltung ist ein Nachrichten- oder Informationskanal mit nur einem Endpunkt, so dass Sender und Empfänger identisch sind. 
In der Kommunikationstechnologie werden Loopbacks gewöhnlich benutzt, um die Erreichbarkeit eines Ziels zu prüfen.

 
 ### Private IP-Adressen
 Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Private_IP-Adresse)
 > Private IP-Adressen (abgekürzt Private IP) sind IP-Adressen, die von der IANA nicht im Internet vergeben sind. Sie wurden für die private Nutzung aus dem öffentlichen Adressraum ausgespart. Als die IP-Adressen des Internet Protokolls v4 knapp wurden und dadurch eine bewusste Einsparung öffentlicher IP-Adressen notwendig wurde, war es umso wichtiger, private IP-Adressen in lokalen Netzwerken zur Verfügung zu haben, die beliebig oft bzw. in beliebigen Netzwerken genutzt werden können.
 
 ### Ping
 Der **ping** Befehl ist ein Tool, mit dem man überprüfen kann, ob ein Host in einem IP-Netzwerk erreichbar ist. Der Teilnehmer, der es überprüfen will,  versendet ein ICMP-Pakete an den anderen Netzwerkteilnehmer (er pingt ihn an). Der angepingte Teilnehmer beantwortet diese Anfrage und somit ist die Frage der Erreichbarkeit geklärkt.
 
 ## Verbinden mit dem Partner
 Wir mussten die Raspberrys mit einem LAN-Kabel miteinander verbinden. Mit dem Kommando **ip addr show** konnten wir die aktuellen Schnittstellen sehen mit den dazugehörigen IP-Adressen.
  ```bash
  michael@michael-GL752VW:~$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0f1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 70:8b:cd:24:5b:de brd ff:ff:ff:ff:ff:ff
3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether b8:8a:60:64:a7:35 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.5/24 brd 10.0.0.255 scope global dynamic noprefixroute wlp2s0
       valid_lft 83229sec preferred_lft 83229sec
    inet6 fe80::bf71:d65:3007:b4ab/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
```

