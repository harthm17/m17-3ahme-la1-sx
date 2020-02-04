# Protokoll 3 La1/SX 3AHME (2019/20)

--------------

* **Thema:** Dienst bei Systemstart starten, Log-Dateien, Login mit Zertifikaten

  * **Datum:** 3.2.2020

  * **Gefehlt:** Niemand

  * **Erstellt von:** Michael Ully

  --------------------------------------------------

  ## Inhaltsverzeichnis

  1.  [Erstellen von C Programmen auf dem Raspberry](#erstellen-von-c-programmen-auf-dem-raspberry)
  
  2. [rc.local](#rc.local)
  
  3. [Service Units](#service-units)
  
  4. [Programme automatisch starten](#programme-automatisch-starten)

  5.  [GNU-Project](#gnu-project)
    * [GNU-Compiler](#gnu-compiler)
 

  ---------------------------------------------------------------
  ## Dienst bei Systemstart automatisch starten lassen
  
  Mit dem Befehl systemctl und der Option enable können wir Dienste bei Systemstart automatisch starten lassen.
  Laut [Wikiubuntuusers](https://wiki.ubuntuusers.de/systemd/systemctl/)
  
  > enable UNITDATEI:	Aktiviert die Unit-Datei UNITDATEI. Danach kann die zugehörige Unit automatisch (z.B. beim Systemstart) gestartet werden.
  
 ```
  bash
  michael@michael-GL752VW:/var/log$ systemctl enable programm
Created symlink /etc/systemd/system/multi-user.target.wants/programm.service → /etc/systemd/system/programm.service.
 ```
