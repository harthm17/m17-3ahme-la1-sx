# Protokoll Labor 3AHME (2020-01-27)

* Thema: Raspberry programmieren
* Datum: 27.01.2020
* Gefehlt:  -
* Erstellt von: strmam17
* Protokoll letzte Einheit: [3.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/strmam17/strmam17/protokolle/protokoll_2020-01-20_strmam17.md)
* Protokoll nächste Einheit: [5.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/strmam17/strmam17/protokolle/protokoll_2020-02-03_strmam17.md)
---------------------------------------------------------------------------------------
## Inhaltsverzeichnis
1. [Portnummer](#portnummer)
2. [Programmiersprachen](#programmiersprachen)
3. [Richard Stallman](#richard-stallman)
4. [C-Programm erstellen](#c-programm-erstellen)
    * [Programm ausführen](#programm-ausführen)
5. [Servicedienst](#servicedienst)
---------------------------------------------------------------------------------------
## Portnummer
Da wir über das Netzwerk den Raspberry programmieren braucht man nicht nur eine IP-Adresse sondern auch eine Portnummer. Die Portnummer der SSH ist immer 22 

---------------------------------------------------------------------------------------
## Programmiersprachen

Die heute häufigsten Programmiersprachen für den Raspberry sind:  

* Phyton
* C
* C++
* Java
* Typescript 
                                                                  
                                                                 
![Programmiersprachen](http://sogrady-media.redmonk.com/sogrady/files/2018/03/lang.rank_.118-1024x726.png)
Quelle: http://sogrady-media.redmonk.com/sogrady/files/2018/03/lang.rank_.118-1024x726.png

---------------------------------------------------------------------------------------
## Richard Stallman
> Richard Matthew Stallman (* 16. März 1953 in Manhattan, auch unter den Initialen rms bekannt) ist ein US-amerikanischer Aktivist und Programmierer, der nach eigenen Angaben im September 1983 die Freie-Software-Bewegung gründete. 
Auf Vorträgen, die überwiegend von der Free Software Foundation organisiert werden, formuliert Stallman vier Freiheiten, mit denen er Freie Software definiert: Die Freiheit, Software nach eigenen Wünschen einzusetzen, den Programmcode zu sichten und nach den eigenen Bedürfnissen zu verändern, mit der Software anderen zu helfen und das Programm verändert weiter zu verbreiten. Für Stallman ist dies eine ethische Notwendigkeit. Durch die Gründung des GNU-Projekts und die Entwicklung des GNU C Compilers, des GNU Debuggers, verschiedener Werkzeuge der GNU coreutils und des Editors GNU Emacs galt er als einer der einflussreichsten und produktivsten Programmierer. Seit 2008 trägt er nicht mehr aktiv zur Programmierung von Software-Projekten bei, sondern ist mehr als Befürworter und Verfechter rund um Freiheitsrechte bei Software involviert (durch Präsentationen, Kampagnen usw.)
Quelle: https://de.wikipedia.org/wiki/Richard_Stallman

---------------------------------------------------------------------------------------
## C-Programm erstellen
  Einloggen auf seinen Raspberry 
      
      ssh strmam17@10.200.114.217
  
  Abfragen wo man sich befindet
  
      pwd
      
  Verzeichnis erstellen 
    
      mkdir programm
      
  Verzeichnis wechseln
  
      cd programm/
      
  C-Programm erstellen
  
      nano main.c
      
Beispiel programm:
      
```c 
      #include  <stdio.h>
      #include  <unistd.h>
      
      int main()
      {
        int cnt=0;
        
        for(int i=0; i<10; i++)
        {
          cnt++;
          printf("cnt=%d\n", cnt);
          sleep(1);                     //Verzögerung des zählen
         }
         return 0;
       }
``` 
## Programm ausführen
Um das Programm ausführen zu können muss man es zuerst Compilieren und das macht man mit dem GNU-Compiler.

  Version vom GNU-Compiler

      gcc --version
    
  Compilieren 
  
      gcc main.c
     
  Programm aufrufen
  
     ./a.out 

Danach machten wir noch eine Zeitverzögerung des zählen wie man im oberen C-programm erkennen kann machten wir es einmal mit sleep und mit delay aber da delay mehr Rechenleistung brauchte machten wir es mit sleep.

  Abfrage von Rechenleistung
      
      top

---------------------------------------------------------------------------------------
## Servicedienst
Wir wollten dass das Programm automatisch startet. Es gibt zwei Varianten entweder rc.local oder systemd. Wir machten es mit systemd, da rc.local sehr veraltet ist und es sehr lange beim Hochfahren dauert.

Service units schreiben
    
    systemd
      
Eigenen Dienst anlegen

    cd /etc/systemd/system
    sudo nano programm.service
    
Beispiel

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
    
Wenn man fertig ist mit programmiern des Raspberrys sollte man es mit dem folgenden Befehl beenden

    sudo poweroff
    
    
