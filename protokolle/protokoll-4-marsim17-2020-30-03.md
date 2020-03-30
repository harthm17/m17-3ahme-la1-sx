# Protokoll LA1/SX 3AHME (2019/20)

* **Thema:** Deamons
* **Datum:** 30.03.2020
* **Gefehlt:** -
* **Erstellt von:** Marcher Simon
* **Protokoll letzte Einheit:** [Protokoll 23.03.2020](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/marsim17/protokolle/protokoll-3-marsim17-2020-23-03.md)
---------

## Begriffserklärung
### Unter Linux
Unter Linux werden die Prozesse vom Kernel in 3 Unterkategorien: Interaktive Prozesse, Bash Prozesse, und [Deamons](https://en.wikipedia.org/wiki/Daemon_(computing)#Unix-like_systems). Deamons sind Hintergrundprozesse, die von anderen Prozessen benötigt werden. Sie werden automatisch beim Booten gestartet und werden erst beim Herunterfahren wieder beendet.

### Unter Java
Ein Deamon Thread in Java ist ein spezieller thread der die JVM nicht daran hindert zu schließen. Auf der anderen Seite gibt es die High-Priority Threads, die zuerst schließen müssen bevor die JVM es tut. Alle Threads innerhalb der main() Methode sind zum Beispiel High-Priority Threads. Ein Beispiel eines Deamons-Threads ist der Garbage Collector. 

## Erstellen eines eigenen Deamons
Der C-Quellcode für den eigenen Deamons ist:
```C
#include <stdio.h>
#include <stdlib.h>
#include <syslog.h>
#include <unistd.h>

int main () {
    openlog ("mydaemon", LOG_PID, LOG_DAEMON);

    syslog (LOG_NOTICE, "mydaemon started.");
    printf("Hello 1\n"); fflush(stdout);
    sleep (2);
    printf("Hello 2\n"); fflush(stdout);
    sleep (2);
    printf("Hello 3\n"); fflush(stdout);
    sleep (2);
    syslog(LOG_WARNING, "bin bei der letzten Ausgabe...");
    printf("Hello 4\n"); fflush(stdout);

    usleep(1000);
    syslog (LOG_NOTICE, "mydaemon terminated.");
    closelog();
    usleep(1000);

    return 0;
}
```

Zum Erstellen des Programs muss man folgende Vorgehensweise befolgen:  
  Ins gesünschte Verzeichnis wechseln  
  `mkdir mydeamon && cd mydeamon`  
  `touch mydeamon.c && nano mydeamon.c`  
  Mit `Ctrl`+`Shift`+`V` kann der Quelltext aus der Zwischenablage eingefügt werden.  
  Mit `Ctrl`+`S` speichert man und mit `Strg`+`X` schließt man den Editor.  
  `gcc -o mydeamon mydeamon.c`  
  
Zum Testen des Programms muss man `./mydeamon` ausführen. Das Ergebnis nach 6 Sekunden sollte folgendermaßen aussehen:  
```console
[simon@simon mydeamon]$ ./mydeamon 
Hello 1
Hello 2
Hello 3
Hello 4
```
Nach dem Beenden sollten auch die Nachrichten im Log stehen. Das kann man mit dem Befehl `journalctl` überprüfen. Brauchbare Parameter sind `-f` um nur die aktuellsten Einträge anzuzeigen, `-p 4`, um nur Warnungen anzuzeigen und `-o verbose`, um mehr Informationen anzeigen zu lassen. Weitere Informationen findet man unter `man journalctl`.  
Der Output von `journalctl -f` ist unter anderem:  
```console
Mar 30 17:05:55 simon mydaemon[5684]: mydaemon started.
Mar 30 17:06:01 simon mydaemon[5684]: bin bei der letzten Ausgabe...
Mar 30 17:06:01 simon mydaemon[5684]: mydaemon terminated.
```
