# Protokoll Raspberry PI

-----

**Name**: Gschier Michael    
**Datum**: 24.02.2020  
**Klasse**: 3AHME  
**Gruppe**: 1  

-----

## Inhaltsverzeichniss

1) [ATmel 324P](#atmel324P)
1) [Raspberry PI](#raspberrypi)  
1) [Linux Debian System](#linuxdebiansystem)
1) [Diverse Operationen](#diverseoperationen)
   * [Über SSH mit Raspberry verbinden](#übersshmitraspberryverbinden)
   * [Programme updaten](#programmeupdaten)
   * [Programme installieren](#programmeinstallieren)
   * [screen](#screen)
   * [User hinzufügen](#userhinzufügen)
   * [Hostname ändern](#hostnameändern)
   * [Sonstiges](#sonstiges)
   * [SSH Schlüssel](#sshschlüssel)

-----

## ATmel 324P
```
• Bit µc
• single chip computer
• 32 KiB Flash (programme)
• 2 KiB SRAM
• Stromverbrauch: 1mW ~ 10 mW
• Preis 1€ ~ 3€
```

* Ein wesentlicher vorteil dieser µc`s ist die Echtzeitfähigkeit!  

-----

## Raspberry PI

```
• 32 oder 64 Bit-System
• Stromverbrauch: 1W ~ 2W
• Preis: 30€ ~ 40€
• Leistungsstarke CPU
• Internetanschluss (ethernet, W-Lan)
• Flash MMC (8/16/32GiB)
• 10000 fach schneller als ATmel 324P
```

-----

## Linux Debian System

* total freie Software...Raspian  
* Ubuntu  

*Ein Man-in-the-Middle-Angriff (MITM) ist ein Angriff, bei dem der Angreifer heimlich die Kommunikation zwischen zwei Parteien,   die glauben, dass sie direkt miteinander kommunizieren, weiterleitet und möglicherweise verändert.*  

**Quelle:** https://en.wikipedia.org/wiki/Man-in-the-middle_attack  

![Bild](https://www.imperva.com/learn/wp-content/uploads/sites/13/2017/09/man-in-the-middle-mitm-attack.png)  



**Quelle:** https://www.imperva.com/learn/wp-content/uploads/sites/13/2017/09/man-in-the-middle-mitm-attack.png

-----

## Diverse Operationen

### Über SSH mit Raspberry verbinden:
```
• ssh benutzer@ipadresse
• standartpassword von raspberry eingeben
• mit passwd password ändern
• mit sudo raspi-config kommt man in die Einstellungen
```

### Programme updaten
```
• sudo -i
• apt update
• apt upgrade
```

### Programme installieren
```
• sudo -i
• apt search programm (z.B. apt search java)
• apt install programm (z.B. apt install screen; apt install default-jre)
```

### screen
```
Mit einem screen kann man Prozesse auch weiterlaufen lassen, wenn man sich ausloggt.
• screen ............... screen erstellen
• screen -r .......... screen wieder anzeigen
```

### User hinzufügen
```
• adduser username
• less /etc/group....... bei sudo Benutzername hinzufügen
```

### Hostname ändern
```
• nano /etc/hostname
• nano /etc/hosts
```

### SSH Schlüssel
```
• ssh-keygen
• ssh-copy-id benutzer@ipadresse
```
