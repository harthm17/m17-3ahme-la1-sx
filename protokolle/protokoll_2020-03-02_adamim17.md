# Protokoll 2020.03.020
-------------------------------
**Programm ausführen am Raspberry Pi**  
**Protokollführer: Mike Adam**  
**Datum: 02.03.2020**

--------------------------------
## Inhaltsverzeichnis:


## Anlegen von einem Kürzel für schnelleres einloggen:
* Als ersten Schritt haben wir uns angemeldet.
````
bsp. schueler@pcxx:~$ SSH adamim17@10.200.114.229
````
* Als nächstes haben wir in der .ssh Datei ein Kürzel für den Benutzer erstellt.
````
bsp. schueler@pcxx:~$ nano .ssh/config
````
* Nun können wir mit dem folgendem Befehl schnell und einfach in der Raspberry Pi einsteigen.   
(Die Nummer des Raspberry Pi war 29, darum der name pi29)   
````
bsp. schueler@pcxx:~$ ssh pi29
````
## Erstellen und Ausführen von einem C - Programm am Raspberry Pi

### Erstellen:

* Als erstes war ein Verzeichnis zu erstellen, wo die Dateien vom Programm gespeichert werden.
````
bsp. adamim17@pi29:~$ mkdir Uebungsprogramm
````
* Um die Dateien hinein zu speihern müssen wir uns im Ordner befinden.
````
bsp. adamim17@pi29:~$ cd Uebungsprogramm
````
* Nun haben wir eine Textdatei im Ordner erstellt.
````
bsp. adamim17@pi29:~$ nano main.c
````
* Jetzt mussten wir das gewünschte C - Programm schreiben.

Diese Option ist nicht empfelenswert, weil der Raspberry Pi dauerhaft belastet wird.
````
#include <stdio.h>

int main()
{
      int i = 100 x 10 + 27;
      printf("i = %d", i);
      for(long l = 0; l < 100000; l++)
      {
      i++;
      printf("i = %d", i);
      }
      return 0;
 }
````
Mit der Lösung wird der Raspberry Pi nicht so stark belastet.
````
#include <stdio.h>
#include <unistd.h>

int main()
{
      int i = 100 x 10 + 27;
      printf("i = %d", i);
      for(long l = 0; l < 100000; l++)
      {
      i++;
      printf("i = %d", i);
      sleep(1);
      }
      return 0;
 }
````

### Ausführen:

* Um das Programm ausführen zu können, muss man es erst Compilieren.
````
bsp. adamim17@pi29:~$ gcc main.c
````
**Dafür wird der GNU - Compiler benutzt:**
> GCC wird von einer Reihe von Systemen als Standardcompiler genutzt, darunter viele Linux-Distributionen, BSD-Varianten, NextStep, BeOS und ZETA. Zudem bietet er auch Unterstützung für die Laufzeitumgebung Cygwin und die Entwicklerwerkzeuge MinGW.[4] Er wurde auf mehr Systeme und Rechnerarchitekturen portiert als jeder andere Compiler und bietet sich besonders für Betriebssysteme an, die auf verschiedenen Hardware-Plattformen laufen sollen. Der GCC lässt sich auch als Cross-Compiler installieren
Wenn keine weiteren Meldungen in der Konsole angezeigt werden, ist das Program fehlerfrei, andernfalls steht der Fehlercode in der Konsole.

* Wenn alles ohne fehler geklappt hat, dann kann man das Programm mit dem folgendem Befehl ausführen.
````
bsp. adamim17@pi29:~$ main.c ./a.out
````
Mit der Tastenkombination **strg + c** kann man das Programm, das ausgeführt wird beenden.

## Log eines C - Programmes:

* Als erstes mussten wir eine log datei erstellen.
* Bevor wir das machen können, müssen wir uns als Superuser anmelden.
````
bsp. adamim17@pi29:~$ sudo -i
````
````
bsp. adamim17@pi29:~$ touch var/log/programm.log
````
* Nachdem die Datei erstellt wurde, haben wir die Rechte verändert, dass wir immer auf die Datei zugreifen können.
````
bsp. adamim17@pi29:~$ chmod 666 var/log/programm.log
````
### Überwachen einer C - Datei:
* Das Programm kann man mit folgendem Befehl überwachen:
````
bsp. adamim17@pi29:~$ watch var/log/programm.log
````
````
bsp. adamim17@pi29:~$ tail -f var/log/programm.log
````
### Logrotate:
Die Log - Dateien werden nach der Zeit immer voller bis es keinen Platz mehr gibt. Logrotate ist eine Sicherheitsmaßnahme dafür.   
* Für diese Befehle muss man sich als Superuser anmelden:
````
bsp. adamim17@pi29:~$ sudo -i
````
* Nachdem wechselt man zur log datei:
````
bsp.  adamim17@pi29:~$ cd /etc/logrotate.d
      adamim17@pi29:/etc/logrotate.d# nano programm
````

* In die Datei wird folgendes eingefügt:
````
{
   rotate 4
   weekly
}
````






