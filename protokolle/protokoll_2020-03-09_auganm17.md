# Protokoll Raspberry PI

-----

**Name**: Andreas Augustin  
**Datum**: 09.03.2020  
**Klasse**: 3AHME  
**Gruppe**: 1  

-----

## Inhaltsverzeichniss

1) [Daten vom Raspberry kopieren](#daten-vom-Raspberry-kopieren)
1) [Startup Systeme](#startup-systeme)
1)
1)

-----

# Daten vom Raspberry kopieren

Es ist vorteilhaft wenn man, bevor man etwas kopiert, in das ```tmp``` verzeichniss wechselt da dieser Ordner bei jedem PC-Neustart gelöscht wird.  

```
schueler@pcxx:~$ cd /tmp
```
```
schueler@pcxx:~$ rsync -aP pi21:/home/auganm17 ./
```

rsync ist ein Programm, um Dateien zwischen lokalen oder über das Netzwerk erreichbaren Pfaden abzugleichen. Dabei werden zunächst die Größe und die Änderungszeit der Dateien in Quelle und Ziel verglichen ("Quick Check"-Algorithmus), so dass nur die Dateien behandelt werden müssen, bei denen es Änderungen gegeben hat. Sind Quelle und Ziel lokale Pfade, werden die betroffenen Dateien normal kopiert. Wenn auf Quelle oder Ziel aber per SSH oder über einen speziellen rsync-daemon zugegriffen wird, nutzt rsync zusätzlich noch einen speziellen Delta-Transfer-Algorithmus, so dass nur die geänderten Teile der Dateien über das Netzwerk transportiert werden müssen.

>Aufgrund dieser Eigenschaften ist rsync sehr gut geeignet, um Sicherungen durchzuführen. Für regelmäßige automatisierte Sicherungen eignen sich Programme wie rsnapshot oder Back In Time, die ihrerseits wieder rsync verwenden. Wenn man allerdings Verzeichnisse zwischen zwei Systemen wie Laptop und Desktop-Rechner synchronisieren möchte, sind Programme wie Unison besser geeignet.
