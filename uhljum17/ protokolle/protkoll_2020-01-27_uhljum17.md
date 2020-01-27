# 3. Protopkoll

------------------------------

* **Thema:** Raspberry, Arduino, Rasperry einrichten
* **Datum:** 27.01.2020
* **Gefehlt:** -
* **Gruppe:** 4
* **Protkollverfasser:** Uhl Julian
* **Letztes Protokoll:** [3. Protokol](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/uhljum17/uhljum17/%20protokolle/protkoll_2020-01-20_uhljum17.md)
* **Nächstes Protkoll:**

-----------------------

# Inhaltsverzeichnis

--------------------------

## SSH

Wir haben ein C Programm in der Shell geschrieben welches wir auf unseren Raspberry laufen lassen wollen und das es sich beim           Hochfahren Startet.

Mit -x kann man den Desktop auf den Raspberry Speigeln, dass geht aber nur z.B. mit den xeyes. Denn ein C_PRogramm braucht immer Prozessor, darum ginge das in Uúnseren Fall nu rR mit Crosscompiler, dafür muss aber auf dem Raspberry eine Volle Version laufen (Desktopversion).

### Programm schreiben

1. **Anmelden**

       ssh uhljum17@10.200.114.227
       
       pw: Eingeben
       
     Verzeichnis erstellen
     
       mkdir programm 
       
     Ins Verzeichnis wechseln 
     
       cd programm/
       
     Programm schreiben
        
       nano main.c
        
     Programm ersetzten/bauen
     
       gcc main.c
       
     Unser Programm
     
     
       
       
       
       
       
       
