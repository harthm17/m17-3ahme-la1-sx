# 6. Protokoll
---------------------

* **Thema:** 
* **Datum:** 10.02.2020
* **Gefehlt:** Strohtiegl, Wade 
* **Gruppe:** 4
* **Protkollverfasser:** Uhl Julian
* **Letztes Protokoll:** [5. Protokol](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/uhljum17/uhljum17/%20protokolle/protokoll_2020-02-03_uhljum17.md)

------------------------------

# Inhalsverzeichnis

------------------------------

  ## Programme installieren
  
  ### APT
  Laut [Wikipedia](https://de.wikipedia.org/wiki/Advanced_Packaging_Tool)
  > Das Advanced Packaging Tool (APT) ist ein Paketverwaltungssystem, das im Bereich des Betriebssystems Debian entstanden ist und dpkg zur eigentlichen Paketverwaltung benutzt. Ziel ist es, eine einfache Möglichkeit zur Suche, Installation und Aktualisierung von Programmpaketen zur Verfügung zu stellen.
  
  **Anwendungsbeispiele:**
  * apt-get update holt die neuesten Informationen über Pakete vom Debian-Server. Sollte man vor apt.get upgrade ausführen.
  * apt-get upgrade bringt, sofern möglich, alle Pakete auf den neuesten Stand, installiert jedoch keine neuen Pakete.
  * apt-get install paketname installiert ein Paket und sämtliche Abhängigkeiten und in der Standardeinstellung zusätzlich empfohlene Pakete.
  
## TCP-Dump
  Mit TCP-Dump kann man kontrolierenwelche Pakete ankommen und weggehen [TCP-Dump](https://wiki.ubuntuusers.de/tcpdump/) installieren
  
  Programm installieren:  
  ```bash
  apt-get install tcpdump
  ```

## Netzwerktechnik

IP-Adresse abfreagen:

````bash
ip addr show
````
oder
````bash
ip a
````

Ausgeben:

````bash
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/127 scope host 
       valid_lft forever preferred_lft forever

       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 08:00:27:66:72:e1 brd ff:ff:ff:ff:ff:ff
    inet 10.1.102.59/24 brd 10.1.102.255 scope global eth0
    inet6 fe80::a00:27ff:fe66:72e1/64 scope link 
       valid_lft forever preferred_lft forever
````

### Loopback

Laut [Wikipedia](https://de.wikipedia.org/wiki/Loopback)

> Ein Loopback oder eine Schleifenschaltung ist ein Nachrichten- oder Informationskanal mit nur einem Endpunkt, so dass Sender und Empfänger identisch sind. 
In der Kommunikationstechnologie werden Loopbacks gewöhnlich benutzt, um die Erreichbarkeit eines Ziels zu prüfen. Auf diese Weise wird sowohl der Nachrichtenkanal zum Ziel als auch das Ziel selbst geprüft. Gewöhnlich besteht der Nachrichtenkanal aus mehreren hintereinanderliegenden Übermittlungsabschnitten. Indem die Schleifenschaltung nacheinander an allen Endpunkten der Übermittlungsabschnitte vorgenommen wird, kann der gesamte Weg bis zum Ziel geprüft werden und eine eventuelle Unterbrechung gefunden werden. Generell gibt es verschiedene Typen von Loopbacks

### Ping 

Laut [Wikipedia](https://de.wikipedia.org/wiki/Ping_(Datenübertragung))

> Ping ist ein Diagnose-Werkzeug, mit dem überprüft werden kann, ob ein bestimmter Host in einem IP-Netzwerk erreichbar ist. Daneben geben die meisten heutigen Implementierungen dieses Werkzeuges auch die Zeitspanne zwischen dem Aussenden eines Paketes zu diesem Host und dem Empfangen eines daraufhin unmittelbar zurückgeschickten Antwortpaketes an

## Raspberry verbinden

um die Raspberries zu verbinden:

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

Aktivieren und deaktivieren mit ip link set (Die Schnittstellen).
```bash 
Uhljum17@pi27:~$ sudo ip link set wlp2s0 down
```
Mit dem Befehl ip a add können wir eine statische IP-Adresse vergeben. /24 ist die Präfixlänge und gibt an wie viele Bits für den Geräte- und den Netzanteil vergeben sind. /24 heißt, dass die ersten 24 Bits der Netzanteil und die letzen acht der Geräteanteil sind. 
```bash
uhljum17@pi27:~$ ip a add 192.168.22.26/27

