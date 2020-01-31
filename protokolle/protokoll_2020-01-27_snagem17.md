# Protokoll Labor/SX 3AHME (2019/20)

* **Thema:** Raspberry Pi Programmieren
* **Datum:** 27.01.2020
* **Gefehlt:** keiner
* **Erstellt von:** Georg Schnabel
* **Protokoll letzte Einheit:** [Protokoll](protokoll_2020-01-20_snagem17.md)

## Inhaltsverzeichnis
1. [SSH](https://de.wikipedia.org/wiki/Secure_Shell)
* Ein C-Programm erstellen
2. Direkter Start beim Hochfahren
* [Runlevel](https://de.wikipedia.org/wiki/Runlevel)

### SSH
In der [SSH](https://de.wikipedia.org/wiki/Secure_Shell) haben wir eine Man-Page aufgerufen und darin ein C-Programm geschrieben, welches Zahlen in einem gewissen Zeitabstand ausgeben soll. Dieses sollte am [Raspberry Pi](https://de.wikipedia.org/wiki/Raspberry_Pi) laufen. Außerdem soll diese Programm beim Hochfahren des PC's direkt starten.

### C-Programm erstellen

**Auf Raspberry zugreifen:** 
```
ssh snagem17@10.200.114.224
```

**Verzeichnis erstellen:**
```
mkdir programm
```
**Ins Verzeichnis wechseln:**
```
cd programm/
```
**C-Programm erstellen:**
```
nano main.c
```

**Unser Programm:**
     ```C
     #include <stdio.h>
     #include <unistd.h>
     
     void delay (int seconds) 
     {
     double x = 0;
     for(int j = 0; j < seconds; j++)
     {
     for(int i = 0; i < 1000; i++)
     {
       x = x +0.1;
       }
      }
     }
     
     int main () 
     {
         int cnt = 0;
         
         for(int i = 0; i < 5000000; i++)
         {
         cnt++;
         printf("cnt=%d\n", cnt);
         sleep(1);
         //delay(1);
         }
        return 0;
     }  
    ``` 
## Direkter Start beim Hochfahren
### Runlevel

[Runlevel](https://de.wikipedia.org/wiki/Runlevel) ist ein Betriebszustand von Computern, der vor allem beim Start des Betriebssystem von Bedeutung ist. 
>Viele Betriebssysteme durchlaufen beim Start (Booten) mehrere abgestufte Systemzustände, bzw. starten in einen bestimmten Zustand, den Runlevel. Jedem Runlevel sind bestimmte System-Dienste zugeordnet, die beim Booten als Prozesse in wohldefinierter Reihenfolge innerhalb des Betriebssystems gestartet werden. Auf diese Weise werden Betriebsmittel des Computers stufenweise in Betrieb genommen.<
Quelle:[Runlevel](https://de.wikipedia.org/wiki/Runlevel)
