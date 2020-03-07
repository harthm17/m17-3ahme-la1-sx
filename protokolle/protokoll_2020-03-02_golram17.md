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
  In dem Verzeichnis ssh werden die Dateien zum einlogge auf dem Computer gespeichert. Die Datei ssh/config speichert sich der Computer die Vereinfachte Version des einloggens.
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
