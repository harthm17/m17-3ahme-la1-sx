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
   * [Verzeichniss erstellen und öffnen](#verzeichniss-erstellen-und-öffnen)
   * [Queltext schreiben](#queltext-schreiben)
   * [Kompelieren](#kompelieren)
    * [Compiler installieren](#compiler-installieren)
   * [Programm ausführen](#programm-ausführen)
   * [In Datei ausgeben](#in-datei-ausgeben)

-----

# Namenskürzel

> Da es umständlich ist bei jedem Login auf dem Raspberry PI den ganzen Namen (ssh auganm17@10.200.114.221) einzugeben kann man man sich ein Kürzel anlegen.

```
nano /ssh/config
    
    Host pi21-root
    Hostname 10.200.114.221
    User root
    
    Host pi21-auganm17
    Hostname 10.200.114.221
    User auganm17
```

> Jetzt hat man in die geöffnete Datei dies reingeschrieben und jetzt kann man sich mit zb: (ssh pi21) einloggen.

-----

# Alias

> Ein Alias ist eine Abkürzung, die man sich selbst festlegen kann, um einen längeren Befehl in der Shell den man häufiger benutzt, schneller und einfacher eingeben kann.

```
alias ll = "ls -al"
```
```
vorher: ls -al
danach: ll
```




-----

# C-Programm erstellen

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

> Bevor man etwas kompelieren kann muss man natürlich einen Compiler (zb: GNU GCC) installieren

```
auganm17@pi21:~ $ apt-get install gcc
auganm17@pi21:~ $ apt-get install libstdc++6-4.6-dev
auganm17@pi21:~ $ sudo apt install build-essential
```

### Programm ausführen





