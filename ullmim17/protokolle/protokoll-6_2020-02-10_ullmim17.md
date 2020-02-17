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
  
