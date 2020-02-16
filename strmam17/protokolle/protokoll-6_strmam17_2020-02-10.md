# Protokoll Labor 3AHME (2020-02-03)
* Thema: Verbinden zweier Raspberrys, Protokolle, Paketverwaltung
* Datum: 10.02.2020
* Gefehlt: Richard Strohrigl, Kilian Wade
* Erstellt von: strmam17
* Protokoll letzte Einheit: [5.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/strmam17/strmam17/protokolle/protokoll-5_strmam17_2020-02-03.md)
* Protokoll nächste Einheit: 
--------------------------------------------------------------------------------

# Inhaltsverzeichnis
1. [Paketliste](#paketliste)
2. [Schnittstellen](#schnittstellen)
    * [Antenne](#antenne)
3. [Protokolle](#protokolle)
4. [Verbinden zweier Raspberrys](#verbinden-zweier-raspberrys)
    * [Statische IP vergeben](#statische-ip-vergeben)
    * [Ping messen](#ping-messen)
    
-------------------------------------------------------------------------------------

## Paketliste 
Man muss die Pakteliste zuerst Aktualisieren um sie aufrufen zu können.

    apt update
    apt list --upgradeable
    apt upgrade
    
Danach haben wir tcpdump (ein Paket-Sniffer) installiert.

    apt install tcpdump
    
------------------------------------------------------------------------------------- 
    
## Schnittstellen
Mithilfe des folgenden Kommando sieht man die ganzen Schnittstellen des Raspberrys.

    ip a show
    
![Raspberry](https://1.bp.blogspot.com/-GD8GID7Ahkw/Wgg6KwZdqtI/AAAAAAAACcQ/0odEaCDHJjsbve_1dG7GlOycDl6tlisIwCLcBGAs/s1600/RaspberryPi-3-Model-B.jpg)

Quelle:https://1.bp.blogspot.com/-GD8GID7Ahkw/Wgg6KwZdqtI/AAAAAAAACcQ/0odEaCDHJjsbve_1dG7GlOycDl6tlisIwCLcBGAs/s1600/RaspberryPi-3-Model-B.jpg
    
## Antenne 

 Vorteil                         | Nachteil
 --------------------------------|-------------------------
 bricht nicht da sie verbaut ist | Reichweite ist nicht gut 
 
 [Loopback](https://de.wikipedia.org/wiki/Loopback)
 
-----------------------------------------------------------------------------------------------------

## Protokolle

1. Ethernet und WLAN Protokoll
   * Verbindung von Computern in einem Netzwerk 
      - unmittelbare Nähe
      
2. IP-Protokoll
   * Verbindung von Computern weltweit
      - Internet ≙ Internationales Netzwerk
      
3. TCP-Protokoll
   * Portnummer vergabe
   
------------------------------------------------------------------------------------------------------

## Verbinden zweier Raspberrys

Wir haben die Raspberrys über das ethernet verbunden [(Subnetz)](https://de.wikipedia.org/wiki/Subnetz). Dann konnten wir wieder mit dem folgenden Kommando die Schnittstellen deines Raspberrys anzeigen lassen.

      ip a show
      
Dort sahen wir eine neu Schnittstelle mit einer IP-Adresse. Mit dem folgenden Kommando kontrollierten wir den ping.

      ping <IP-Adresse des anderen>
      
Wenn der ping ankommt, dann heißt das, dass das Netzwerk funktioniert.


Die Rooter reden über das Internet Control Messagis Protokoll (icmp).

      ping icmp
      
Schnittstelle ein- und ausschalten:

      ip link set eth1 up
      ip link set eth1 down
      
Mac-Adresse vom Verbundenen anzeigen lassen:

      ip n
      
-----------------------------------------------------------------------------------------

## Statische IP vergeben

Statische IP vergben:

      ip a s eth1 
      
öffentliche IPv4 => werden vom Provider vergeben

private IPv4 => 10.0.0.0/8; 172.16.0.0/12; 192.168.0.0/16

10.0.0.0/8 in Binär

Netzwerkadresse | Geräteadresse 
----------------|-------------------------------
0000 1010       | 0000 0000 0000 0000 0000 0000

Das heißt man kann 2^24 -2 Geräte verwenden.


      ip a add <deine IP-Adresse> dev eth1
      ip a show eth1
      
## Ping messen

Messen welche Pakete eintreffen.

      tcpdump --version       // zeigt die Version des tcpdump an
      tcpdump -i eth1
      
Falls die Netzwerkschnittstelle aus ist, dann fragt er nach aber er bekommt nichts zurück da er keine Mac-Adresse hat.
      
