# 4. Protokoll

------------------------------

* **Thema:** Programmiren am Raspberry
* **Datum:** 27.01.2020
* **Gefehlt:** -
* **Gruppe:** 4
* **Protkollverfasser:** Uhl Julian
* **Letztes Protokoll:** [3. Protokol](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/uhljum17/uhljum17/%20protokolle/protkoll_2020-01-20_uhljum17.md)
* **Nächstes Protkoll:**

-----------------------

# Inhaltsverzeichnis

1. [SSH](SSH)
    1. [Programm schreiben](Programm-schreiben)
    2. [Anmelden und Programm schreiben](Anmelden-und-Programm-schreiben)       
    3. [Beim Hochfahren Programm Starten](Beim-Hochfahren-Programm-Starten)
 

--------------------------

## SSH

Wir haben ein C Programm in der Shell geschrieben welches wir auf unseren Raspberry laufen lassen wollen und das es sich beim           Hochfahren Startet.

Mit -x kann man den Desktop auf den Raspberry Speigeln, dass geht aber nur z.B. mit den xeyes. Denn ein C_PRogramm braucht immer Prozessor, darum ginge das in Uúnseren Fall nu rR mit Crosscompiler, dafür muss aber auf dem Raspberry eine Volle Version laufen (Desktopversion).

### Programm schreiben

#### Anmelden und Programm schreiben

1. Folgendes machen:

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
 
#### Beim Hochfahren Programm Starten
 
2. Das das Programm beim beim Hochfahren Startet geht mit 
 
  * rc.local
  
       ![rc.local](http://1.bp.blogspot.com/_ZohlokReQFY/SiHgcAr94nI/AAAAAAAAACc/i8fSbXh2N24/s320/slrl.png)
       
>Viele Betriebssysteme durchlaufen beim Start (Booten) mehrere abgestufte Systemzustände, bzw. starten in einen bestimmten Zustand, den Runlevel. Jedem Runlevel sind bestimmte System-Dienste zugeordnet, die beim Booten als Prozesse in wohldefinierter Reihenfolge innerhalb des Betriebssystems gestartet werden. Auf diese Weise werden Betriebsmittel des Computers stufenweise in Betrieb genommen. Bei Beendigung des Betriebssystems (Shutdown) werden die Runlevel in umgekehrter Reihenfolge durchlaufen, die laufenden Prozesse werden stufenweise beendet, bis der Computer ausgeschaltet werden kann. Daneben kann auch direkter Wechsel von einem Runlevel in einen anderen erfolgen. 
Runlevel kennt man vor allem aus den unterschiedlichen Unix-Systemen wie Solaris (vor Solaris 10), GNU/Linux, HP-UX oder AIX. Doch auch in Windows entsprechen die Startoptionen Abgesicherter Modus, Abgesicherter Modus mit Netzwerk oder Windows normal Starten im Windows-Bootmenü jeweils genau einem Runlevel. Solaris 10 verwendet runlevel nur noch rudimentär, die Hauptsystemsteuerung wird dort durch Service Management Facility (SMF) erledigt. 
Idee der unterschiedlichen Runlevel ist es, Sicherheitsstufen bereitzustellen, in denen nur bestimmte Systemprozesse aktiv sind. Dies ist wichtig, falls beispielsweise ein System von Computerviren befallen ist und ohne Netzwerk-Anbindung laufen soll. 
Im Gegensatz zu den am System V orientierten Betriebssystemen kennt FreeBSD keine Runlevels, sondern hält am traditionellen init von BSD fest. 

Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Runlevel)
 
 
 * man schreibt Service Units
 
   ``` 
   [Unit]
   Description=Labor Programm
   
   [Service]
   Type=simple
   ExecStart=/home/uhljum17/programm/a.out
   
   [Install]
   WantedBY=multi-user.target
    ``` 
       
       ll /etc/systemd/system
       
       cd /etc/systemd/system
       
       sudo nano programm.dervice
       
    Programm starten
       
       sudo systemctl start programm
       
    Status anzeigen lassen
    
       sudo systemctl status programm
    
    Programm stoppen
    
       sudo systemctl stop programm
