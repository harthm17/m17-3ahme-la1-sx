# Protokoll Labor/SX 3AHME (2019/20)

* **Thema:** RaspberryPi Programmieren
* **Datum:** 27.01.2020
* **Gefehlt:** keiner
* **Erstellt von:** Georg Schnabel
* **Protokoll letzte Einheit:** [Protokoll](protokoll_2020-01-20_snagem17.md)

## Inhaltsverzeichnis



     ```C
     #include <stdio.h>
     #include <unistd.h>
     
     void delay (int seconds) {
     double x = 0;
     for(int j = 0; j < seconds; j++){
     for(int i = 0; i < 1000; i++){
       x = x +0.1;
       }
      }
     }
     
     int main () {
         int cnt = 0;
         
         for(int i = 0; i < 5000000; i++){
         cnt++;
         printf("cnt=%d\n", cnt);
         sleep(1);
         //delay(1);
         }
        return 0;
     }  
     ``` 
