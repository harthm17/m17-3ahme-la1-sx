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
  
