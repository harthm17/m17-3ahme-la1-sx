# Protokoll 3 La1/SX 3AHME (2019/20)

--------------

* **Thema:** Dienst bei Systemstart starten, Log-Dateien, Login mit Zertifikaten

  * **Datum:** 3.2.2020

  * **Gefehlt:** Niemand

  * **Erstellt von:** Michael Ully

  --------------------------------------------------

  ## Inhaltsverzeichnis

  1.  [Dienst bei Systemstart automatisch starten lassen](#dienst-bei-systemstart-automatisch-starten-lassen)
  
  2. [Log-Dateien](#log-dateien)
  
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
 ## Log-Dateien
 Laut [ip-insider](https://www.ip-insider.de/was-ist-eine-log-datei-a-794350/)
 
 > Eine Log-Datei ist eine Datei, in der IT-Systeme Ereignisse eintragen und protokollieren. Die Datei soll helfen, bestimmte Vorgänge nachzuvollziehen und kann beispielsweise für die Problemanalyse oder die Rekonstruktion von Transaktionen zum Einsatz kommen. Die Log-Datei ist in der Regel textbasiert.

Weil wir die count-Ausgabe im [journal](https://wiki.ubuntuusers.de/systemd/journald/) nicht gefunden haben, wollten wir die Ausgabe des Dienstes in eine Lod-Datei schreiben.
