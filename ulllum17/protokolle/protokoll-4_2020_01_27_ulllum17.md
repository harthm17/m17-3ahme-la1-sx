# 3. Protokoll | AHME17
# Uller Lucas
--------------------------------------------------------------------------
* **Thema:** Raspberry PI
* **Datum:** 20.01.2020
* **Gefehlt:** ---
* **Erstellt von:** ulllum17
* **Protokoll letzte Einheit:** [3.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/ulllum17/ulllum17/protokolle/protokoll-3_2020-01-20_ulllum17.md) 
* **Protokoll nächste Einheit:**
--------------------------------------------------------------------------
# Inhaltsverzeichnis


--------------------------------------------------------------------------
## SSH
> Secure Shell oder SSH bezeichnet sowohl ein Netzwerkprotokoll als auch entsprechende Programme, 
mit deren Hilfe man auf eine sichere Art und Weise eine verschlüsselte Netzwerkverbindung mit einem entfernten Gerät herstellen kann.
Häufig wird diese Methode verwendet, um lokal eine entfernte Kommandozeile verfügbar zu machen, das heißt, 
auf einer lokalen Konsole werden die Ausgaben der entfernten Konsole ausgegeben und 
die lokalen Tastatureingaben werden an den entfernten Rechner gesendet. Genutzt werden kann dies 
beispielsweise zur Fernwartung eines in einem entfernten Rechenzentrum stehenden Servers. 
Die neuere Protokoll-Version SSH-2 bietet weitere Funktionen wie Datenübertragung per SFTP.
Die IANA hat dem Protokoll den TCP-Port 22 zugeordnet.

Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Secure_Shell)



## Programmieren auf dem PI

Auf dem Raspberry PI gibt es viele Programmiersprachen, da der Raspberry PI ein vollwertiger PC ist.

### Programmiersprachen
* Phython
* C
* C++
* Java

### C-Programm erstellen

````bash
nano main.c
````
### Compilieren

````bash
gcc main.c
````
### Compiliertes Programm ausführen

````bash
./a.out
````
### Regeln für Zeitverzögerung

* die Funktion *sleep* benutzen
