 # Protokoll Labor/SX 3AHME (2019/20) 

* **Thema** : Raspberry PI
* **Datum** : 10.02.2020 
* **Gruppe** : 4 
* **Protokollverfasser** : Christoph Sebernegg 
* **Protokoll letzte Einheit** : [5.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/sebchm17/sebchm17/protokolle/protokoll_2020-02-03_sebchm17.md) 

--------------------------------------------------------------------------------------------------------------------------------------------

## Inhaltsverzeichniss

1. [Mit Partner Raspberry verbinden](mit-partner-raspberry-verbinden)
1. [IP Adressen statisch vergeben](ip-adressen-statisch-vergeben)
1.
1.
1.
1.


--------------------------------------------------------------------------------------------------------------------------------------------

## Mit Partner Raspberry verbinden

Wir verbunden zwei Raspberrys mit dem Ethernetkabel.

Mit folgendem Befehl konnten wir abfragen ob die Schnittstelle funktionstüchtig ist.
      ip a 
      
ping-Befehl

      ping <IP-Adresse des anderen>
      
Ping ist ein Diagnose-Werkzeug, mit dem überprüft werden kann, ob ein bestimmter Host in einem IP-Netzwerk erreichbar ist.


Die Rooter reden über das Internet Control Messagis Protokoll (icmp).

      ping icmp
      
Schnittstelle ein- und ausschalten:

      ip link set eth1 up
      ip link set eth1 down
      
Mac-Adresse vom Verbundenen anzeigen lassen:

      ip n

--------------------------------------------------------------------------------------------------------------------------------------------

## IP Addresse statisch vergeben

Mit folgenden Befehl werden die IP-Adressen statisch vergeben

````bash
ip a s eth1
````

Man muss darauf Achten das man beim Vergeben zwischen privaten IPv4 Adressen und öffentlichen IPv4 Adressen unterscheidet.

privater IPv4 Adressenbereich:

10.0.0.0/8

172.16.0.0/12

192.168.0.0/16


8 | 12 | 16 ist die Netzmaske.
