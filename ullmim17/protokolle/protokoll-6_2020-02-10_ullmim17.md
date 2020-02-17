# Protokoll 6 La1/SX 3AHME (2019/20)

--------------

* **Thema:** Netzwerktechnik mit dem RaspberryPI

  * **Datum:** 10.2.2020

  * **Gefehlt:** Kilian Wade, Richard Strohrigl

  * **Erstellt von:** Michael Ully
  
  * **Letztes Protokoll:** [5. Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/ullmim17/ullmim17/protokolle/protokoll-5_2020-02-03_ullmim17.md)
  
  * **Nächstes Protokoll:**

  --------------------------------------------------

  ## Inhaltsverzeichnis

  1.  [Programme installieren](#programme-installieren)
      1. [APT](#apt)
      
  2. [TCP-Dump](#tcp-dump)
  3. [Netzwerktechnik mit dem Raspberry](#netzwerktechnik-mit-dem-raspberry)
      1. [Netzwerkprotokolle](#netzwerkprotokolle)
      2. [Loopback](#loopback)
      3. [Private IP-Adressen](#private-ip-adressen)
      4. [Ping](#ping)
  4. [Verbinden mit dem Partner](#verbinden-mit-dem-partner)
    

  
 

  ---------------------------------------------------------------
  
  ## Programme installieren
  
  ### APT
  Laut [Wikipedia](https://de.wikipedia.org/wiki/Advanced_Packaging_Tool)
  > Das Advanced Packaging Tool (APT) ist ein Paketverwaltungssystem, das im Bereich des Betriebssystems Debian entstanden ist und dpkg zur eigentlichen Paketverwaltung benutzt. Ziel ist es, eine einfache Möglichkeit zur Suche, Installation und Aktualisierung von Programmpaketen zur Verfügung zu stellen.
  
  **Anwendungsbeispiele:**
  1) apt-get install paketname installiert ein Paket und sämtliche Abhängigkeiten und in der Standardeinstellung zusätzlich empfohlene Pakete.
  2) apt-get upgrade bringt, sofern möglich, alle Pakete auf den neuesten Stand, installiert jedoch keine neuen Pakete.
  3) apt-get update holt die neuesten Informationen über Pakete vom Debian-Server. Sollte man vor apt.get upgrade ausführen.
  
  ## TCP-Dump
  Wir wollten uns das Kommandozeilenprogramm [TCP-Dump](https://wiki.ubuntuusers.de/tcpdump/) installieren. Mit diesem Programm     kann man kontrollieren, welche Pakete am eigenen Rechner ankommen und weggeschickt werden.
  
  Wir haben das Programm mit dem Befehl atp-get install installiert.
  ```bash
  apt-get install tcpdump
  ```
  ## Netzwerktechnik mit dem Raspberry
  
  ### Netzwerkprotokolle
  Laut [ipinsider](https://www.ip-insider.de/was-ist-ein-netzwerk-protokoll-a-711459/)
  > Netzwerk-Protokolle regeln den Datenaustausch in Computernetzen. Sie definieren die erforderlichen Regeln für Aufgaben wie das Adressieren von Datenpaketen, die Vermittlung von Datenpaketen, den Transport von Datenpaketen, den Verbindungsaufbau oder die Fehlerüberprüfung. Wichtige Netzwerk-Protokolle für das Internet sind in der IP-Protokollfamilie zu finden.
  
  Es gibt zum Beispiel das TCP-Protokoll, das dafür sorgt, dass Programme Daten miteinander austauschen können und diese in richtiger Reihenfolge und fehlerfrei ankommen. Das IP-Protokoll ermöglicht das Verbinden von Computern weltweit. Es gibt verschiedene Versionen z.B IPv4 und IPv6. Dann gibt es noch das Ethernet/WLAN-Protokoll, das die Verbindung von Computern in einem Netzwerk in unmittelbarer Nähe ermöglicht.
  
  ### Loopback
  Laut [Computerweekly](https://www.computerweekly.com/de/definition/Loopback-Test)
  > Bei einem Loopback-Test wird von einem Kommunikationsgerät ein Testmuster gesendet und dann an es zurückgegeben (Schleifentest). So lässt sich herausfinden, ob das Gerät angemessen funktioniert. Weiterhin können Administratoren damit überprüfen, welcher Knotenpunkt oder Node im Netzwerk ausgefallen ist.

 >Eine Form des Loopback-Tests funktioniert mithilfe eines Sondersteckers, der sich Rückkopplungsstecker oder Wrap Plug     nennt. Dieser wird in einen Port des Kommunikationsgerätes eingesteckt. Im Endeffekt soll der Rückkopplungsstecker bewirken,  dass übertragene (Output) Daten als empfangene (Input) Daten zurückkommen. Somit wird ein kompletter Kommunikationsschaltkreis mithilfe eines einzelnen Computers simuliert.
 ### Private IP-Adressen
 Laut [Wikipedia](#https://de.wikipedia.org/wiki/Private_IP-Adresse)
 > Private IP-Adressen (abgekürzt Private IP) sind IP-Adressen, die von der IANA nicht im Internet vergeben sind. Sie wurden für die private Nutzung aus dem öffentlichen Adressraum ausgespart, damit sie ohne administrativen Mehraufwand (Registrierung der IP-Adressen) in lokalen Netzwerken genutzt werden können. Als die IP-Adressen des Internet Protokolls v4 knapp wurden und dadurch eine bewusste Einsparung öffentlicher IP-Adressen notwendig wurde, war es umso wichtiger, private IP-Adressen in lokalen Netzwerken zur Verfügung zu haben, die beliebig oft bzw. in beliebigen Netzwerken genutzt werden können. (Siehe auch [Port Address Translation](https://de.wikipedia.org/wiki/Port_Address_Translation) und [Network Address Translation](https://de.wikipedia.org/wiki/Netzwerkadress%C3%BCbersetzung))
 ### Ping
 Der ping Befehl ist ein Diagnose Tool mit dem man überprüfen kann, ob ein Host in einem IP-Netzwerk erreichbar ist. Der anpingende Teilnehmer versendet dabei ICMP-Pakete an den angepingenden Netzwerkteilnehmer.Der angepingte Teilnehmer beantwortet diese kurze Anfrage und somit ist die Frage der grundsätzlichen Erreichbarkeit geklärkt. Weiterführende Informationen auf [Wikiubuntuusers](https://wiki.ubuntuusers.de/ping/).
 ## Verbinden mit dem Partner
  Zuerst haben wir die Raspberrys mit einem LAN-Kabel miteinander verbunden. Mit dem Kommando ip addr show konnten wir alle aktuellen Schnittstellen inklusive IP-Adresse sehen.
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
Wir haben gemerkt, dass die angezeigte IP-Adresse vom Partner nicht der Schulnetzwerkadresse entspricht. Das liegt daran, dass über [Zero-Conf](https://de.wikipedia.org/wiki/Zeroconf) automatisch eine IP-Adresse vergeben wurde.

Mit dem Befehl ip link set können wir eine Schnittstelle aktivieren und deaktivieren.
```bash 
michael@michael-GL752VW:~$ sudo ip link set wlp2s0 down
