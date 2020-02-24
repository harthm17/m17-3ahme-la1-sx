 # Protokoll Labor/SX 3AHME (2019/20) 

* **Thema** : Raspberry PI
* **Datum** : 10.02.2020 
* **Gruppe** : 4 
* **Protokollverfasser** : Christoph Sebernegg 
* **Protokoll letzte Einheit** : [5.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/sebchm17/sebchm17/protokolle/protokoll_2020-02-03_sebchm17.md) 

----------------------------------------------------------------------------------------------------------------------------------------------

## Inhaltsverzeichniss

1. [IP Adressen statisch vergeben](ip-adressen-statisch-vergeben)
1.
1.
1.
1.


----------------------------------------------------------------------------------------------------------------------------------------------

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
