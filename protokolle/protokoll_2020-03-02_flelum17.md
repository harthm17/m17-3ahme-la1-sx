# Labor Protokoll 2020-03-03
         
**Lukas Fleischhacker**       
**3AHME**   

----------------------------
## Inhaltsverzeichnis    
1) [Nickname](#nickname)  
   * [Wofür](#wofür)  
   * [Erstellen](#erstellen)   
2) [C-Programm](#c-programm)
   * [Verzeichnis erstellen](#verzeichnis-erstellen)
   * [Quelltext schreiben](#quelltext-schreiben)
   * [Compilieren](#compilieren)
         * [GNU Project](#gnu-project)
   * [Programm ausführen](#programm-ausführen)
3) [Man in the middle](#man-in-the-middle)

----------------------------
## Nickname
### Wofür
Mithilfe eines Nicknames kann man sich schneller und einfacher bei einem Raspberry einloggen.               
Ähnlich wie bei einem Alias verkürtzt man die Eingabe.                  
                  
Früher musste man **ssh flelum17@10.200.114.226** und das Passwort eingeben                                         
Jetzt geht es auch nur mit **ssh pi26**                    

### Erstellen

        nano /ssh/config (die Datei öffnen)
        
        (in die Datei schreiben:)
        
        Host pi26-root
        Hostname 10.200.114.226
        User root
        
        Host pi26-flelum17
        Hostname 10.200.114.226
        User flelum17

## C-Programm
### Verzeichnis erstellen

         flelum17@pi26:~$ mkdir programm              

### Quelltext schreiben

         flelum17@pi26:~$ /programm nano main.c
         
### Compilieren
Mithilfe des *GNU-Compilers*

         flelum17@pi26:~/programm $ gcc main.c

#### GNU Project
         
   >Das GNU-Projekt entwickelt das Betriebssystem GNU (Aussprache: [ɡnuː][1]),                
   das von Richard Stallman mit dem Ziel gegründet wurde, ein freies,               
   unixähnliches Betriebssystem zu schaffen, das sicherstellt,dass die              
   Endbenutzer die Freiheiten haben, es verwenden, untersuchen, verbreiten (kopieren)                 
   und verändern zu dürfen. Software, deren Lizenz diese Freiheiten garantiert, wird                  
   Freie Software (engl. Free Software) genannt, GNU ist in diesem Sinne frei.
 
laut [Wikipedia](https://de.wikipedia.org/wiki/GNU-Projekt)

![Richard Stallman](https://upload.wikimedia.org/wikipedia/commons/thumb/4/46/Richard_Stallman_2005_%28chrys%29.jpg/220px-Richard_Stallman_2005_%28chrys%29.jpg)

Richard Stallman

### Programm ausführen

      flelum17@pi26:~/programm $ ./a.out
      

