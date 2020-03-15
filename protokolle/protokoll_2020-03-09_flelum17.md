# Labor Protokoll 2020-03-09
         
**Lukas Fleischhacker**       
**3AHME**   

----------------------------
## Inhaltsverzeichnis    
1) [Kopie der Raspberry-Dateien](#kopie-der-raspberry-dateien)  
   * [tmp Verzeichnis](#tmp-verzeichnis)  
   * [rsync](#rsync)   

----------------------------

## Kopie der Raspberry-Dateien

### tmp Verzeichnis
Mit ````/tmp```` in das temporäre Verzeichnis wechseln.   
> im Verzeichnis /tmp werden jene Dateien abgelegt, die nach einem Neustart des Systems zweifelsfrei nicht mehr benötigt werden und während des Systemstarts geleert werden können          
    
[laut Wikipedia](https://de.wikipedia.org/wiki/Temporäre_Datei)    

### rsync
Mit ````rsync```` werden die Daten gespeichert. 

    schueler@pcxx:~$ rsync -a pi26:/home/flelum17 ./
    
    
                 
    
