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

Um das Programm ausführen zu können, muss man es erst Compilieren.
````
bsp. adamim17@pi29:~$ gcc main.c
````

