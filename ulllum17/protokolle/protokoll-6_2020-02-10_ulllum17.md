# 6. Protokoll | AHME17 
# Uller Lucas
-------------------------------------------------------------------------
* **Thema:** Raspberry PI, SSH-Verbindungen
* **Datum:** 10.02.2020
* **Gefehlt:** ---
* **Erstellt von:** ulllum17
* **Protokoll letzte Einheit:** [5.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/ulllum17/ulllum17/protokolle/protokoll-5_2020-02-03_ulllum17.md)
--------------------------------------------------------------------------
## Inhaltsverzeichnis

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
install PAKETNAME
````

Mit folgendem Befehl wird die Paketliste angezeigt

````bash
apt list --upgradeable
````

Mit folgendem Befehl werden Installierte Pakete, wenn möglich, auf eine verbesserte Version aktualisiert. Um geänderte Abhängigkeiten zu erfüllen, werden gegebenfalls auch neue Pakete installiert.

````bash
apt upgrade
````

## Netzwerk-Technik

> Ein Computer Netzwerk ist eine Verbund zwischen mehreren Computern (mindestens zwei), die Daten gegeneinander austauschen. Die PCs können praktisch miteinander kommunizieren. Ein Computer Netzwerk hat aber nicht nur den Vorteil das Daten gegeneinander ausgetauscht werden können, sondern auch, dass auf man den gleichen Internetzugang verwendet oder auch einen gemeinsamen Drucker verwendet.

Quelle:[DeinElektriker](https://dein-elektriker-info.de/was-ist-ein-netzwerk/)

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
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 08:00:27:66:72:e1 brd ff:ff:ff:ff:ff:ff
    inet 10.1.102.59/24 brd 10.1.102.255 scope global eth0
       valid_lft forever preferred_lft forever
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

