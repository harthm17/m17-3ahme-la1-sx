# Protokoll Labor/SX 3AHME (2019/20)

* **Thema:** Raspberry Pi Programmieren
* **Datum:** 27.01.2020
* **Gefehlt:** keiner
* **Erstellt von:** Georg Schnabel
* **Protokoll letzte Einheit:** [Protokoll](protokoll_2020-01-20_snagem17.md)

## Inhaltsverzeichnis
1. [Port](https://de.wikipedia.org/wiki/Port_%28Protokoll%29)
2. [Programmiersprachen](https://de.wikipedia.org/wiki/Liste_von_Programmiersprachen)
1. [SSH](https://de.wikipedia.org/wiki/Secure_Shell)
* Ein C-Programm erstellen
2. Direkter Start beim Hochfahren
* [Runlevel](https://de.wikipedia.org/wiki/Runlevel)

### Port
Da wir über die [SSH](https://de.wikipedia.org/wiki/Secure_Shell), gleichzeitig unser Netzwerk, auf unserem Raspberry Pi programmieren, benötigen wir auch eine Portnummer. Diese Potnummer ist beiuns immer die Zahl **22**.

### Programmiersprachen
Man kann Raspberrys in vielen verschiedenen programmiersprachen programmieren. Wir machen das mit der [Programmiersprache C](https://de.wikipedia.org/wiki/C_(Programmiersprache)), da wir erst diese erlernt haben. Man kann es aber auch mit anderen Programmiersprachen tun:
* [Phyton](https://de.wikipedia.org/wiki/Python_%28Programmiersprache%29)
* [C++](https://de.wikipedia.org/wiki/C%2B%2B)
* [Java](https://www.programmierenlernen24.de/java-programmieren-lernen/)
* [Typescript](https://jaxenter.de/typescript-lernen-praxis-63696)

![Quelle](http://sogrady-media.redmonk.com/sogrady/files/2018/03/lang.rank_.118-1024x726.png)
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

## Direkter Start beim Hochfahren
### Runlevel

[Runlevel](https://de.wikipedia.org/wiki/Runlevel) ist ein Betriebszustand von Computern, der vor allem beim Start des Betriebssystem von Bedeutung ist. 
>Viele Betriebssysteme durchlaufen beim Start (Booten) mehrere abgestufte Systemzustände, bzw. starten in einen bestimmten Zustand, den Runlevel. Jedem Runlevel sind bestimmte System-Dienste zugeordnet, die beim Booten als Prozesse in wohldefinierter Reihenfolge innerhalb des Betriebssystems gestartet werden. Auf diese Weise werden Betriebsmittel des Computers stufenweise in Betrieb genommen.<
Quelle:[Runlevel](https://de.wikipedia.org/wiki/Runlevel)
