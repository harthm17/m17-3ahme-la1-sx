# Protokoll 4 La1/SX 3AHME (2019/20)

-------------------------

* **Thema:** Erstellen und Starten von C -Programmen auf dem Raspberry PI
  * **Datum:** 02.03.2020
  * **Gefehlt:** ---
  * **Erstellt von:** Golser Raphael
  
  -------------------------------------------------------
  
## Inhaltsverzeichnis

1.  [Einsteigen in den Rapberry PI mit dem key](#einsteigen-in-den-raspberry-pi-mit-dem-key)
2.  [Erstellen von C-Programmen im Raspberry PI](#erstellen-von-c-programmen-im-raspberry-pi)
3.  [Die Veränderung des C-Programms im log sehen](#die-veränderung-des-c-programms-im-log-sehen)
5.  [Das GNU-Project](#das-gnu-project)

-----------------------------------------------

  ## Einsteigen in den Raspberry PI mit dem key
  
  In der letzten Einheit hatten wir ein keypaar auf unseren Computern erstellt und nun wollen wir uns mithilfe der keys in unsere Raspberry PIs einloggen. Mit diesem Befehl taten wir das:
  ````bash
  schueler@pcxx:~$ ssh golram17@10.200.114.225
  ````
  Um das Einloggen zu erleichtern haben wir eine Datei angelegt in der wir die Daten die wir zum einloggen benötigten reinschrieben. 
  ````bash
  schueler@pcxx:~$ nano .ssh/config
  ````
  In dem Verzeichnis ````.ssh/config```` werden die Dateien zum einloggen auf dem Computer gespeichert. Die Datei ````.ssh/config ````speichert sich nun der Computer die Vereinfachte Version des einloggens.
  ````bash
  schueler@pcxx:~$ ssh pi25
  ````
  Nun hatten wir es so eingestellt das wir mit ````ssh pi25```` uns direkt mit dem superuser einloggen.
  ````bash
  schueler@pcxx:~$ ls -la
  schueler@pcxx:~$ nano .ssh/config
  schueler@pcxx:~$ ssh pi25
  ````
  Zuerst wurden alle Dateien in Listenform angezeigt um zu sehen wo die Datei .ssh zu finden ist. Danach haben wir die Datei .ssh/config geändert und die Nicknamen so geändert das ````ssh pi25````uns in unsere eigenen Usern auf dem Raspberry einloggt und ````ssh pi25-root````in den Superuser.
  
--------------------------------------------------------------------------------------------------------

  ## Erstellen von C-Programmen im Raspberry PI

Mit dem Befehl ````mkdir```` haben wir im home Verzeichnis ein weiteres Verzeichnis erstellt:
````bash
golram17@pi25:~$ mkdir programm
````
Nun wir haben wir einen Alias für ````ls -al```` erstellt um dies schneller auszuführen:
````bash
golram17@pi25:~$ alias "ll = ls -al"
````
Nun gingen wir in unser erstelltes Verzeichnis hinein:
````bash
golram17@pi25:~$ cd programm
````
In diesem haben wir ein C-Programm erstellt:
````
golram17@pi25:~$ nano main.c
````
Nun wollten wir unser Programm im Terminal nochmals sehen:
````
golram17@pi25:~$ cat main.c
#include <stdio.h>

int main(){
      int i;
      i = 100;
      return 0;
}
````
Um dieses Programm ausführen zu können muss man dies zuerst compilieren und für dieses wird dann eine ````a.out```` Datei erstellt:
````bash
golram17@pi25:~$ gcc main.c
````
Nun wollen wir das Programm zuerst umschreiben so dass das Programm etwas sichtbares tut und danach auch noch ausführen:
````
golram17@pi25:~$ nano main.c
golram17@pi25:~$ cat main.c
#include <stdio.h>
#include <unistd.h>

int main(){
      int i = 100 x 10 +27;
      printf("i = %d", i);
      for(long l = 0; l < 100000; l++){
         /* i++;
         printf("i = %d", i);
         schlechte Lösung weil der Raspberry PI auf dauer belastet wird*/
         i++;
         printf("i = %d", i);
         sleep(1);//Bessere Lösung weil Raspberry nicht auf dauer Belastet wird
      }
      return 0;
 }
 golram17@pi25:~$ gcc main.c
 golram17@pi25:~$ ./a.out
 ````
 mit ````./````können wir Programme ausführen und mit ````strg + c```` können wir das ausgeführte Programm beenden.
 
 ------------------------------------------------------
 
 ## Die Veränderung des C-Programms im log sehen
 
 Um dies zu tun mussten wir einmal das Verzeichnis für die logdateien suchen:
 ````bash
 golram17@pi25:~$ ll /var/log
 ````
 Nachdem wir keine Datei fanden haben wir eine erstellt:
 ````bash
 golram17@pi25:~$ sudo touch /var/log/programm.log
 ````
 Nun konnten wir aber die Datei nicht bearbeiten weil nur bisher der Superuser Änderungsrechte hat. Deshalb mussten wir die Rechte ändern:
 ````bash
 golram17@pi25:~$ sudo chmod 666 /var/log/programm.log
 ````
 Die eingabe ````666```` bedeutet das der Superuser und wir alle Rechte haben. 
 Jetzt wollten wir die letzten Werte unseres C-Programms in dieser Datei sehen:
 ````bash
 golram17@pi25:~$ watch ls -l /var/log/programm.log
 ````
 Nun sehen wir zwar die letzten Werte aber nicht die die in diesem Zeitpunkt erstellt werden.
 Jetzt werden wir die Datei so öffnen dass sie sich immer updatet und den neuesten Wert des C-Programms anzeigt:
 ````bash
 golram17@pi25:~$ tail -f /var/log/programm.log
 ````
 Um nun alle Änderung sehen zu können müssen wir in dem Verzeichnis ````log````eine andere Datei öffnen:
 ````bash
 golram17@pi25:~$ sudo less -S /var/log/syslog
 ````
 Jedoch werden jetzt die logdateien voll und das ist schlecht weshalb wir in einem neuen Verzeichnis eine Sicherungsmaßnahme erstellen:
 ````
 golram17@pi25:~$ sudo -i
 root@pi25:~# cd /etc/log
 root@pi25:~# cd /etc/lograte.c
 root@pi25:~# cd /etc/lograte.d/
 root@pi25:~# ll
 root@pi25:~# ls -l (weil noch kein alias bei andere Konsole erstellt)
 root@pi25:~# nano programm
 ````
 In das Programm wurde einen rotation hineingeschrieben damit das log Verzeichnis jede Woche entleert wird:
 ````
 {
    rotate 4
    weakly
 }
 ````
 Nun als Zusatz haben wir gelernt wie man die history vom Raspberry in eine Datei auf dem Computer in das temporäre Verzeichnis speichert:
 ````bash
 schueler@pcxx:~$ scp pi25-root: /root.bash_history/tmp
 ````
 
 ---------------------------------------------------------
 
 ## Das GNU-Project
 
 Laut [Wikipedia](https://de.wikipedia.org/wiki/GNU-Projekt)
>Das GNU-Projekt entwickelt das Betriebssystem GNU (Aussprache: [ɡnuː][1]), das von Richard Stallman mit dem Ziel gegründet wurde, ein freies, unixähnliches Betriebssystem zu schaffen, das sicherstellt, dass die Endbenutzer die Freiheiten haben, es verwenden, untersuchen, verbreiten (kopieren) und verändern zu dürfen. Software, deren Lizenz diese Freiheiten garantiert, wird Freie Software (engl. Free Software) genannt, GNU ist in diesem Sinne frei.
Bekanntheit erlangte das Projekt vor allem auch durch die von ihm eingeführte GNU General Public License (GPL), unter der viele weitere Softwareprojekte veröffentlicht werden, sowie zahlreiche GNU-Programme wie die GNU Compiler Collection, der GNU Debugger sowie Werkzeuge der GNU Core Utilities, der Editor Emacs und andere.

### GNU-Compiler
Laut [Wikipedia](https://de.wikipedia.org/wiki/GNU_Compiler_Collection)
>GCC ist der Name der Compiler-Suite des GNU-Projekts. GCC stand ursprünglich für GNU C Compiler. Da GCC heute aber außer C noch einige andere Programmiersprachen übersetzen kann, hat GCC inzwischen die Bedeutung GNU Compiler Collection erhalten (englisch für GNU-Compilersammlung). Das Kommando gcc (in Kleinbuchstaben) steht weiterhin für den C-Compiler.
 
 ![Richard Stallman](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a8/Richard_Stallman_at_CommonsFest_Athens_2015_2.JPG/295px-Richard_Stallman_at_CommonsFest_Athens_2015_2.JPG)

*Richard Stallman*

