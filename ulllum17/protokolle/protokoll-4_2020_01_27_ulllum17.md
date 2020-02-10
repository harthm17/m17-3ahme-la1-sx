# 4. Protokoll | AHME17
# Uller Lucas
--------------------------------------------------------------------------
* **Thema:** Raspberry PI
* **Datum:** 20.01.2020
* **Gefehlt:** ---
* **Erstellt von:** ulllum17
* **Protokoll letzte Einheit:** [3.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/ulllum17/ulllum17/protokolle/protokoll-3_2020-01-20_ulllum17.md) 
* **Protokoll nächste Einheit:** [5.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/ulllum17/ulllum17/protokolle/protokoll-5_2020-02-03_ulllum17.md)
--------------------------------------------------------------------------
# Inhaltsverzeichnis
1. [SSH](#ssh)    
1. [Programmieren auf dem PI](#programmieren-auf-dem-pi)   
1. [Zeitverzögerung](#zeitverzögerung)   
1. [Service Unit](#service-unit)   
    1. [Dienst anlegen](#dienst-anlegen)   
    1. [Service Unit Ausführen](#service-unit-ausführen)  
1. [Herunterfahren vom PI](#herunterfahren-vom-pi)  
    


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

### Beispiel

````c
      #include  <stdio.h>
      #include  <unistd.h>
      
      int main()
      {
        int cnt=0;
        
        for(int i=0; i<10; i++)
        {
          cnt++;
          printf("cnt=%d\n", cnt);
          sleep(1);                     //Verzögerung des zählen
         }
         return 0;
       }
````

### Compilieren

````bash
gcc main.c
````
### Compiliertes Programm ausführen

````bash
./a.out
````
### Zeitverzögerung
**sleep(1) vs. delay**

|sleep(1)|delay|
|:------:|:---:|
|Programm wird in eine art Tiefschlaf versetzt|Programm berechnet unötig etwas --> Rechenleistungsverschwendung|

## Service Unit

Dieser Dienst dienen dazu, Dienste zu starten und zu stoppen - und entsprechen damit den früheren Init-Skripten von SysVinit bzw. Archiv/Upstart. Zur Steuerung dient der systemd-eigene Befehl systemctl.

### Dienst anlegen

**Verzeichnis aufrufen**

````bash
cd /etc/systemd/system
````
**Service Unit erstelle**

````bash
sudo nano programm.service
````

**Minimale Service Unit**

````bash
[Unit]
Description=Labor Programm

[Service]
Type=simple
ExecStart=/home/ulllum17/programm/a.out

[Install]
WantedBy=multi-user.target
````

> Der Schlüssel ExecStart enthält den Befehl zum Starten des Dienstes. Wichtig ist, dass immer der volle Pfad zum Befehl angegeben wird. In diesem Abschnitt kann z.B. auch eingetragen werden, welche Befehle vor oder nach dem Start des eigentlichen Services ausgeführt werden sollen, unter welchem Benutzer und welcher Gruppe der Dienst läuft (Standard: root). Außerdem wird hier festgelegt, welchen Typ der Service haben soll. Das Type=simple im obigen Beispiel müsste nicht explizit angegeben werden, da dies der Vorgabewert ist.

Quelle [Service Units](https://wiki.ubuntuusers.de/systemd/Service_Units/)


### Service Unit Ausführen

**start**
````bash
sudo systemctl start programm
````
**stop**
````bash
sudo systemctl stop programm
````

### Herunterfahren vom PI

Das der PI ordungsgemäß abgeschaltet wird sollte man folgendne Befehl benutzen.

````bash
poweroff
````
