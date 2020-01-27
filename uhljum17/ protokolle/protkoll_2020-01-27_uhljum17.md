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

1. **Anmelden und Programm schreiben**

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
     
     ```C
     #include <stdio.h>
     #include <unistd.h>
     
     void delay (int seconds) {
     double x = 0;
     for(int j = 0; j < seconds; j++){
     for(int i = 0; i < 1000; i++){
       x = x +0.1;
       }
      }
     }
     
     int main () {
         int cnt = 0;
         
         for(int i = 0; i < 5000000; i++){
         cnt++;
         printf("cnt=%d\n", cnt);
         sleep(1);
         //delay(1);
         }
        return 0;
     }  
     ```     
 
 2. **Beim Hochfahren Programm Starten**
 
 Das das Programm beim beim Hochfahren Startet geht mit 
 
  * rc.local
  
![rc.local](http://1.bp.blogspot.com/_ZohlokReQFY/SiHgcAr94nI/AAAAAAAAACc/i8fSbXh2N24/s320/slrl.png)
       
