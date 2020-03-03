# Raspberry#2
## Inhaltsverzeichniss
1) [Nickname](#nickname)
     * [Nickname erstellen](#nickname-erstellen)
2) [C-Programm](#c-programm)
     * [C-Programm in Terminal erstellen](#c-programm-in-terminal-erstellen)
          * [Ordner erstellen](#ordner-erstellen)
          * [Quelltext schreiben](#quelltext-schreiben)
          * [Kompellieren](#textdatei-in-programm-umwandeln)
          * [Programm ausführen](#programm-ausführen)
          * [Ausgabe in einer Datei](#ausgabe-in-einer-datei)
               

## Nickname
### Nickname erstellen:
Ein Nickname hat Ähnlichkeiten mit einem alias. In unserem Fall hilft er indem wir uns nun noch schneller in unseren Raspberry einloggen können.
1. Die Datei *.ssh/config* öffnen (z.B. nano /ssh/config)
2. Folgendes in die Datei eintregen:
 
 ```
 Host pi16-root
 Hostname 10.200.114.222
 User root 
 
 Host pi16-root
 Hostname 10.200.114.222
 User root 
 ```  
 Nun kann man indem man **ssh pi16** eingiebt, sich mit dem Raspberry sehr einfach verbinden.
   
## C-Programm
### C-Programm in Terminal erstellen:
#### Ordner erstellen
``` 
fucnim17@pi22:~ $ mkdir programm
```
#### Quelltext schreiben
```
fucnim17@pi22:~ $ /programm nano main.c
```
#### Textdatei in Programm umwandeln:
mit Compiler (z.B. GNU Compiler) 
![](https://upload.wikimedia.org/wikipedia/en/thumb/2/22/Heckert_GNU_white.svg/1200px-Heckert_GNU_white.svg.png =250x)
--> [GNU Project](https://de.wikipedia.org/wiki/GNU-Projekt)
```
fucnim17@pi22:~/programm $ gcc main.c--
```
#### Programm ausführen: 
```
fucnim17@pi22:~/programm $ ./a.out
```
#### Ausgabe in einer Datei:

ls -al /var/log
sudo touch /var/log/programm.log
sudo chmod 666/var/log/programm.log
ls -al /var/log/programm.log
gcc main.c
./a.out

Datei "überwachen":
fucnim17@pi22:~ $ watch ls -l /var/log/programm.log

oder

fucnim17@pi22:~ $ tail -f /var/log/programm.log


Logrotate

root@pi22:~# cd /etc/logrotate.d
root@pi22:/etc/logrotate.d# nano programm

folgendes eingeben:::
/var/log/programm.log
{ 
  rotate 4
  weekly
}












