 # Protokoll Labor/SX 3AHME (2019/20) 


* **Thema** : Raspberry PI 
* **Datum** : 27.01.2020 
* **Gruppe** : 4 
* **Protokollverfasser** : Christoph Sebernegg 
* **Protokoll letzte Einheit** : [3.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/sebchm17/sebchm17/protokolle/protokoll_2020-01-20_sebchm17.md) 

-------------------------------------------------------------------------------------------------------------------------------- 

## Inhaltsverzeichnis 

1.  [Programmiersprachen](#programmiersprachen)
1.  [Portnummern](#portnummern)
1.  [Richard Stallman](#richard-stallman)
1.  [Über SSH einsteigen](#über-ssh-einsteigen) 
1.  [C-Programm erstellen, compelieren und ausführen](#c-programm-erstellen-compelieren-und-ausführen) 
1.  [Autostartprogramm erstellen](#autostartprogramm-erstellen) 

--------------------------------------------------------------------------------------------------------------------------------- 

 ## Programmiersprachen
 Das Wort PI im Namen vom Raspberry steht für Pyhton. Pyhton ist eine Programmiersprache.
 Weitere Programiersprachen ür den Raspberry:
* C
* C++
* Java
* Typescript
 
 
 ![Programmiersprachen](http://sogrady-media.redmonk.com/sogrady/files/2018/03/lang.rank_.118-1024x726.png)
 
---------------------------------------------------------------------------------------------------------------------------------

## Portnummern

Die Standardportnummer der SSH ist 22. Wir brauchen diese, weil wir über das Netzwerk den Raspberry programmieren.

Eine Portnummer ist allgemein der Teil einer Netzwerk-Adresse, der die Zuordnung von TCP- und UDP-Verbindungen und -Datenpaketen zu Server- und Client-Programmen durch Betriebssysteme bewirkt.

---------------------------------------------------------------------------------------------------------------------------------

## Richard Stallman
>Richard Matthew Stallman (* 16. März 1953 in Manhattan, auch unter den Initialen rms bekannt) ist ein US-amerikanischer Aktivist und Programmierer, der nach eigenen Angaben im September 1983 die Freie-Software-Bewegung gründete.
Auf Vorträgen, die überwiegend von der Free Software Foundation organisiert werden[2], formuliert Stallman vier Freiheiten, mit denen er Freie Software definiert: Die Freiheit, Software nach eigenen Wünschen einzusetzen, den Programmcode zu sichten und nach den eigenen Bedürfnissen zu verändern, mit der Software anderen zu helfen und das Programm verändert weiter zu verbreiten.[1] Für Stallman ist dies eine ethische Notwendigkeit.[3][4][5][6][7][8] Durch die Gründung des GNU-Projekts und die Entwicklung des GNU C Compilers, des GNU Debuggers, verschiedener Werkzeuge der GNU coreutils und des Editors GNU Emacs galt er als einer der einflussreichsten und produktivsten Programmierer.[9] Seit 2008 trägt er nicht mehr aktiv zur Programmierung von Software-Projekten bei, sondern ist mehr als Befürworter und Verfechter rund um Freiheitsrechte bei Software involviert (durch Präsentationen, Kampagnen usw.

Quelle: https://de.wikipedia.org/wiki/Richard_Stallman

---------------------------------------------------------------------------------------------------------------------------------

## Über SSH einsteigen

    schueler@pcxx:~$ ssh sebchm@10.200.114.216
    sebchm@10.200.114.216's password: 

---------------------------------------------------------------------------------------------------------------------------------

## C-Programm erstellen, compelieren und ausführen

    sebchm@pi16:~ $ mkdir programm 

Zuerst erstellen wir ein verzeichnis, um dort das C-Programm zu speichern.

    sebchm@pi16:~/programm $ nano main.c 

```C  #include  <stdio.h>
      #include  <unistd.h>
      
      int main()
      {
        int cnt=0;
        
        for(int i=0; i<10; i++)
        {
          cnt++;
          printf("cnt=%d\n", cnt);
          sleep(1);                    
         }
         return 0;
```       
Das ist das Programm das wir gemeinsam schrieben. Es zählt von 1 bis 10. sleep verzögert das zählen.

Programm compelieren:
Standardcompieler GNU

    sebchm@pi16:~/programm $ gcc main.c 

Programm ausführen:

    sebchm@pi16:~/programm $ ./a.out 


---------------------------------------------------------------------------------------------------------------------------------

## Autostartprogramm erstellen

Um das Programm automatisch starten zu lassen gibt es zwei Möglichkeiten. 1. mit rc.local aber diese Methode ist sehr veraltet. 2.mit systemd. Wir verwendeten systemd, weil die andere Methode zu lange beim hochfahren brauchen würde.

Service schreiben
    
    systemd
      
Dienst anlegen

    cd /etc/systemd/system
    sudo nano programm.service
    
Das ist die Service-Datei

    [Unit]
    Description=Labor Programm
    
    [Service]
    Type=simple
    ExecStart=/home/strmam17/programm/a.out
    
    [Install]
    WantedBy=multi-user.target
    
Programm starten 
  
    sudo systemctl start programm
   
Programm stoppen

    sudo systemctl stop programm
    
Den Raspberry mit dem folgenden Befehl verlassen.

    sudo poweroff

---------------------------------------------------------------------------------------------------------------------------------
