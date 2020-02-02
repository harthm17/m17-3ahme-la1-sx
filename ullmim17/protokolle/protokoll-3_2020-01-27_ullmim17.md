# Protokoll 3 La1/SX 3AHME (2019/20)

--------------

* **Thema:** Erstellen von C Programmen auf dem Raspberry und das automatische Starten lassen von Programmen

  * **Datum:** 27.1.2020

  * **Gefehlt:** Niemand

  * **Erstellt von:** Michael Ully

  --------------------------------------------------

  ## Inhaltsverzeichnis

  1.  [Erstellen von C Programmen auf dem Raspberry](#erstellen-von-c-programmen-auf-dem-raspberry)

  2.  [GNU-Project](#gnu-project)
    * [GNU-Compiler](#gnu-compiler)
  3.  [Raspberry Name und Passwort ändern und Benutzer erstellen](#raspberry-name-und-passwort-ändern-und-benutzer-erstellen)

  4.  [Man in the middle](#man-in-the-middle)

  ----------------------

  ## Erstellen von C Programmen auf dem Raspberry

  In dieser Laboreinheit wollten wir C-Programme auf dem Raspberry erstellen und diese anschließend automatisch starten lassen.

  

  1) Zuerst haben wir uns wieder über SSH mit dem Raspberry verbunden. Will man sich über SSH mit dem Raspberry verbinden braucht man die IP-Adresse und die Portnummer. Die Portnummer der SSH ist immer 22.

  

 ````bash

michael@michael-GL752VW:~$ ssh pi@10.200.114.222

````
2) Dann haben wir im home Verzeichnis mit dem Befehl mkdir ein Verzeichnis mit dem Namen programm angelegt.
 ````bash

michael@michael-GL752VW:~$ mkdir programme


````
3) Als nächstes haben wir mit dem Texteditor Nano ein C Programm geschrieben, das Zahlen von 1 bis 1000 ausgibt.
 ````bash

michael@michael-GL752VW:~$ nano main.c

````
C-Code:
````C
#include <stdio.h>

int main(){
        int cnt=0;

        for(int i=0;i<1000;i++)
        {
                cnt++;
                printf("cnt:%d\n",cnt);
        }
}

````
4) Das Programm muss natürlich noch kompiliert werden. Wir haben den GNU-Compiler verwendet.
````bash
michael@michael-GL752VW:~$ gcc main.c
````
5) Gibt man nun das Verzeichnis und den Dateinamen in die Kommandozeile ein kann man das Programm starten.
````bash
michael@michael-GL752VW:~$ ./a.out
cnt:1
cnt:2
...
cnt:1000
````
6) Dann wollten wir noch eine Verzögerung von 1 Sekunde nach jeder Ausgabe einbauen. Das haben wir mit der Funktion sleep() gelöst, diese gibt dem Betriebssystemkernel die Anweisung das Programm für eine gewisse Zeit zu pausieren. Ansonsten könnte man noch mit einer Schleife, die unnötig Rechenleistung verbraucht eine Verzögerung realisieren(nicht zu empfehlen).
```C
#include <stdio.h>
#include <unistd.h>
int main(){
        int cnt=0;

        for(int i=0;i<10;i++)
        {
                cnt++;
                printf("cnt:%d\n",cnt);
                sleep(1);
        }
}
```
## GNU-Project
Laut [Wikipedia](https://de.wikipedia.org/wiki/GNU-Projekt)
>Das GNU-Projekt entwickelt das Betriebssystem GNU (Aussprache: [ɡnuː][1]), das von Richard Stallman mit dem Ziel gegründet wurde, ein freies, unixähnliches Betriebssystem zu schaffen, das sicherstellt, dass die Endbenutzer die Freiheiten haben, es verwenden, untersuchen, verbreiten (kopieren) und verändern zu dürfen. Software, deren Lizenz diese Freiheiten garantiert, wird Freie Software (engl. Free Software) genannt, GNU ist in diesem Sinne frei.
Bekanntheit erlangte das Projekt vor allem auch durch die von ihm eingeführte GNU General Public License (GPL), unter der viele weitere Softwareprojekte veröffentlicht werden, sowie zahlreiche GNU-Programme wie die GNU Compiler Collection, der GNU Debugger sowie Werkzeuge der GNU Core Utilities, der Editor Emacs und andere.

### GNU-Compiler
Laut [Wikipedia](https://de.wikipedia.org/wiki/GNU_Compiler_Collection)
>GCC ist der Name der Compiler-Suite des GNU-Projekts. GCC stand ursprünglich für GNU C Compiler. Da GCC heute aber außer C noch einige andere Programmiersprachen übersetzen kann, hat GCC inzwischen die Bedeutung GNU Compiler Collection erhalten (englisch für GNU-Compilersammlung). Das Kommando gcc (in Kleinbuchstaben) steht weiterhin für den C-Compiler.
