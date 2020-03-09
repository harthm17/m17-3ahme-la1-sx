# Protokoll Raspberry PI

-----

**Name**: Andreas Augustin  
**Datum**: 03.03.2020  
**Klasse**: 3AHME  
**Gruppe**: 1  

-----

## Inhaltsverzeichniss

1) [Namenskürzel](#namenskürzel)
1) [C-Programm erstellen](#c-programm-erstellen)  
1) [Alias](#alias)  
1) [C Programm erstellen](#c-programm-erstellen)
   * [Verzeichniss erstellen und öffnen](#verzeichniss-erstellen-und-öffnen)
   * [Queltext schreiben](#queltext-schreiben)
   * [Kompelieren](#kompelieren)
       * [Compiler installieren](#compiler-installieren)
   * [Programm ausführen](#programm-ausführen)
   * [In Datei ausgeben](#in-datei-ausgeben)
   * [Datei überwachen](#datei-überwachen)
   * [Logrotate](logrotate)
       * [In Datei schreiben](#in-datei-schreiben)

-----

# Namenskürzel

Da es umständlich ist bei jedem Login auf dem Raspberry PI den ganzen Namen (ssh auganm17@10.200.114.221) einzugeben kann man man sich ein Kürzel anlegen.

```
nano /ssh/config
    
    Host pi21-root
    Hostname 10.200.114.221
    User root
    
    Host pi21-auganm17
    Hostname 10.200.114.221
    User auganm17
```

Jetzt hat man in die geöffnete Datei dies reingeschrieben und jetzt kann man sich mit zb: (ssh pi21) einloggen.

-----

# Alias

Ein Alias ist eine Abkürzung, die man sich selbst festlegen kann, um einen längeren Befehl in der Shell den man häufiger benutzt, schneller und einfacher eingeben kann.

```
alias ll = 'ls -al'
```
```
vorher: ls -al
danach: ll
```
Dieser Alias ist allerdings nur ein vorübergehender Alias und existiert beim nächsten Start der shell nicht mehr! Um ihn dauerhaft anzulegen muss man in die ".bashrc" Datei.

-----

# C Programm erstellen

-----

### Verzeichniss erstellen und öffnen

```
auganm17@pi21:~ $ mkdir Programm
auganm17@pi21:~ $ cd Programm
auganm17@pi21:~/programm $ nano main.c
```

-----

### Queltext schreiben

zb:
```
#include <stdio.h>

int main () {

	int i;

	i = 100 * 10 + 27;
	printf ("i = %d\n", i);

	return 0;
}
```
> strg O --> speichern  
strg X --> Texteditor beenden

-----

### Kompelieren

```
auganm17@pi21:~/programm $ gcc main.c--
```

-----

### Compiler installieren

Bevor man etwas kompelieren kann muss man natürlich einen Compiler (zb: GNU GCC) installieren

```
auganm17@pi21:~ $ apt-get install gcc
auganm17@pi21:~ $ apt-get install libstdc++6-4.6-dev
auganm17@pi21:~ $ sudo apt install build-essential
```
>Das GNU-Projekt entwickelt das Betriebssystem GNU, das von Richard Stallman mit dem Ziel gegründet wurde, ein freies, unixähnliches Betriebssystem zu schaffen, das sicherstellt, dass die Endbenutzer die Freiheiten haben, es verwenden, untersuchen, verbreiten (kopieren) und verändern zu dürfen. Software, deren Lizenz diese Freiheiten garantiert, wird Freie Software (engl. Free Software) genannt, GNU ist in diesem Sinne frei.

>Bekanntheit erlangte das Projekt vor allem auch durch die von ihm eingeführte GNU General Public License (GPL), unter der viele weitere Softwareprojekte veröffentlicht werden, sowie zahlreiche GNU-Programme wie die GNU Compiler Collection, der GNU Debugger sowie Werkzeuge der GNU Core Utilities, der Editor Emacs und andere.

**GNU Projekt:** https://de.wikipedia.org/wiki/GNU-Projekt

-----

### Programm ausführen

auganm17@pi21:~/programm $ ./a.out

-----

### In Datei ausgeben

Der Text wird nicht mehr im Terminal, sondern in einer Datei ausgeben.

```
auganm17@pi21:~ $ ll /var/log
auganm17@pi21:~ $ sudo touch /var/log/programm.log
auganm17@pi21:~ $ sudo chmod 666/var/log/programm.log
auganm17@pi21:~ $ ll /var/log/programm.log
auganm17@pi21:~ $ gcc main.c
auganm17@pi21:~ $ ./a.out
```

-----

### Datei überwachen

Um eine Datei zu überwachen gibt es zwei funktionierente Befehle:

```
auganm17@pi21:~ $ watch ll /var/log/programm.log
```
```
auganm17@pi21:~ $ tail -f /var/log/programm.log
```

-----

### Logrotate

> logrotate wurde entwickelt, um die Verwaltung von Systemen zu erleichtern, die eine große Anzahl von Protokolldateien erzeugen. Es ermöglicht das automatische Drehen, Komprimieren, Entfernen und Versenden von Protokolldateien. Jede Protokolldatei kann täglich, wöchentlich, monatlich oder wenn sie zu groß wird, bearbeitet werden.

Normalerweise wird Logrotate als täglicher Cron-Job ausgeführt. Er ändert ein Protokoll nicht mehrmals an einem Tag, es sei denn, das Kriterium für dieses Protokoll basiert auf der Größe des Protokolls und Logrotate wird mehrmals täglich ausgeführt, oder es wird die Option -f oder --force verwendet. 

**Quelle:** https://linux.die.net/man/8/logrotate

```
root@pi21:~# cd /etc/logrotate.d  
root@pi21:~ /etc/logrotate.d nano programm   
```
##### In Datei schreiben
```
/var/log/programm.log
     { 
     rotate 4
     weekly
     }
```

