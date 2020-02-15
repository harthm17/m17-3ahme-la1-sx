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


 
 
 
