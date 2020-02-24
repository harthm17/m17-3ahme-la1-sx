 # Protokoll Labor/SX 3AHME (2019/20) 

* **Thema** : Raspberry PI
* **Datum** : 10.02.2020 
* **Gruppe** : 4 
* **Protokollverfasser** : Christoph Sebernegg 
* **Protokoll letzte Einheit** : [5.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/sebchm17/sebchm17/protokolle/protokoll_2020-02-03_sebchm17.md) 

--------------------------------------------------------------------------------------------------------------------------------------------

## Inhaltsverzeichniss

1. [APT Paketliste](apt-paketliste)
1. [Mit Partner Raspberry verbinden](mit-partner-raspberry-verbinden)
1. [Netzwerktechnik](netzwerktechnik)
1. [Netzwerk Protokolle](netzwerk-protokolle)
1. [IP Adressen statisch vergeben](ip-adressen-statisch-vergeben)
1. [

--------------------------------------------------------------------------------------------------------------------------------------------

## APT Paketliste

Neueinlesen der Paketlisten
```
apt update
```

Paketname instalieren
```
apt install <Paketname>
```

Anzeigen der Paketliste
```
apt list --upgradeable
```

Updaten der Paketlisten
````bash
apt upgrade
````

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

## Netzwerktechnik

Mit ``ip addr show `` kann die IP-Adresse abgefragt werden.

Ausgabe:

````bash
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever

       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 08:00:27:66:72:e1 brd ff:ff:ff:ff:ff:ff
    inet 10.1.102.59/24 brd 10.1.102.255 scope global eth0
    inet6 fe80::a00:27ff:fe66:72e1/64 scope link 
       valid_lft forever preferred_lft forever
````

--------------------------------------------------------------------------------------------------------------------------------------------

## Netzwerk Protokolle

* TCP-Protokoll
   * Portnummern vergabe, für die Programm zuordnung    


* Ethernet und Wlan Protokoll
   * Verinden von Computer, im Lokalen Netzwerk
   
* IP-Protokoll
   * Verbinden von Computer, im Internet    
   
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
