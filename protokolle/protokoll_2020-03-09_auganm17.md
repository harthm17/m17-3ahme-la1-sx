# Protokoll Raspberry PI

-----

**Name**: Andreas Augustin  
**Datum**: 09.03.2020  
**Klasse**: 3AHME  
**Gruppe**: 1  

-----

## Inhaltsverzeichniss

1) [Daten vom Raspberry kopieren](#daten-vom-raspberry-kopieren)
1) [Startup Systeme](#startup-systeme)
1) [systemd](#systemd)
1) [C Programm atomatisch starten](#c-programm-automatisch-starten)
1) [Java Programm automatisch starten](#java-programm-automatisch-starten)
1) [Komprimieren](#komprimieren)
    * [Windows](#windows)
    * [Ubuntu](#ubuntu)

-----

# Daten vom Raspberry kopieren

Es ist vorteilhaft wenn man, bevor man etwas kopiert, in das ```tmp``` verzeichniss wechselt da dieser Ordner bei jedem PC-Neustart gelöscht wird.  

```
schueler@pcxx:~$ cd /tmp
```

Hier wird alles, wo es veränderungen gab, kopiert und nichts wird gelöscht.

```
schueler@pcxx:/tmp$ rsync -aPn pi21:/home/auganm17 ./
```

Mit ```-aPn``` kann man im Terminal anschauen was kopiert werden würde.

```
schueler@pcxx:/tmp$ rsync -aPn pi21:/home/auganm17 ./
```

>rsync ist ein Programm, um Dateien zwischen lokalen oder über das Netzwerk erreichbaren Pfaden abzugleichen. Dabei werden zunächst die Größe und die Änderungszeit der Dateien in Quelle und Ziel verglichen ("Quick Check"-Algorithmus), so dass nur die Dateien behandelt werden müssen, bei denen es Änderungen gegeben hat. Sind Quelle und Ziel lokale Pfade, werden die betroffenen Dateien normal kopiert. Wenn auf Quelle oder Ziel aber per SSH oder über einen speziellen rsync-daemon zugegriffen wird, nutzt rsync zusätzlich noch einen speziellen Delta-Transfer-Algorithmus, so dass nur die geänderten Teile der Dateien über das Netzwerk transportiert werden müssen.

>Aufgrund dieser Eigenschaften ist rsync sehr gut geeignet, um Sicherungen durchzuführen. Für regelmäßige automatisierte Sicherungen eignen sich Programme wie rsnapshot oder Back In Time, die ihrerseits wieder rsync verwenden. Wenn man allerdings Verzeichnisse zwischen zwei Systemen wie Laptop und Desktop-Rechner synchronisieren möchte, sind Programme wie Unison besser geeignet.

**Quelle:** [wiki](https://wiki.ubuntuusers.de/rsync/)

-----

# Startup Systeme

>Der Linux-Startprozess ist der mehrstufige Initialisierungsprozess, der während des Bootens einer Linux-Installation durchgeführt wird. Er ähnelt in vielerlei Hinsicht dem BSD- und anderen Unix-ähnlichen Startprozessen, von denen er abgeleitet ist.

>Das Booten einer Linux-Installation umfasst mehrere Stufen und Softwarekomponenten, darunter die Initialisierung der Firmware, die Ausführung eines Boot-Loaders, das Laden und Starten eines Linux-Kernel-Images und die Ausführung verschiedener Startskripte und Daemons. Für jede dieser Phasen und Komponenten gibt es verschiedene Variationen und Ansätze; so können z.B. GRUB, LILO, SYSLINUX oder Loadlin als Bootloader verwendet werden, während die Startskripte entweder im traditionellen Init-Stil ausgeführt werden können oder die Systemkonfiguration durch moderne Alternativen wie systemd oder Upstart durchgeführt werden kann. 

**Quelle:** [Wikipedia](https://en.wikipedia.org/wiki/Linux_startup_process)

-----

# systemd

>systemd ist ein System- und Sitzungs-Manager (Init-System), der für die Verwaltung aller auf dem System laufenden Dienste über die gesamte Betriebszeit des Rechners, vom Startvorgang bis zum Herunterfahren, zuständig ist. Prozesse werden dabei immer (soweit möglich) parallel gestartet, um den Bootvorgang möglichst kurz zu halten.

**Quelle:** [wiki](https://wiki.ubuntuusers.de/systemd/)

Mit ```systemctl``` ruft man den systemd Befehl auf. Mit Status lässt sich der status des ausgewählten Programms anzeigen.

```
root@pcxx:~# systemctl status alsa-state
```

Lässt man den Programmnamen weg bekommt man den Status des Computers.

```
root@pcxx:~# systemctl status
```

Um Programme starten oder stoppen zu können, muss man der Superuser sein.


```
root@pcxx:~# systemctl stop alsa-state
```
&

```
root@pcxx:~# systemctl start alsa-state
```

Man kann eine zweite Konsole starten und sich alle änderungen LIVE anzeigen lassen. Das hat den Vorteil, dass man nicht immer ```systemctl status``` eingeben muss um zu sehen ob die Änderungen wirksam waren.

```
root@pcxx:~# journalctl -f /alsa-state
```

-----

# C Programm automatisch starten

Programm:
```c
int main ()
{
    int counter = 0;
    for (int i = 0; i < 10; i++)
    {
        counter += i;
        printf("%d\n", counter);
    }
    
    return 0;
}
```

Zuerst muss man eine Service Datei erstellen

```
root@pi21:~# nano /etc/systemd/system/auganm17-programm.service
```

In die Datei schreibt man folgendes:

```
[Unit]
Description=C-Programm mit Ausgabe

[Service]
ExecStart=/home/fucnim17/programm/a.out

[Install]
WantedBy=multi.user.target
```

Jetzt würde schon alles funktionieren jedoch muss man das ganze noch aktivieren um es bei jedem PC-Neustart automatisch starten zu lassen.

```
root@pi21:~# systemctl enable auganm17-programm
```

Um alles wirksam zu machen muss man den Raspberry Neustarten

```
root@pi21:~# reboot
```

-----

# Java Programm automatisch starten

Programm:
```java
public class Main {
    
    private static int counter; //Zählereigenschaft
    
    public static void main (String[] args) {
        for (int i = 0; i < 10; i++) {
            counter += i;
            System.out.println(counter);
        }
    }
}
```

Zuerst muss man das Java-Programm auf den Raspberry kopieren:

```
schueler@pcxx:~$ rsync -aP /schreibtisch/java_3ahme_auganm17.tar.xz pi21 /tmp/
```

Dann muss man, gleich wie bei einem C-Programm, eine Service Datei erstellen

```
root@pi21:~# nano /etc/systemd/system/auganm17-programm.service
```

In die Datei schreibt man folgendes:

```
[Unit]
Description=Java Programm mit Ausgabe

[Service]
ExecStart=java -jar /root/Java_auganm17_3ahme.jar

[Install]
WantedBy=multi-user.target
```

Jetzt muss man das ganze wieder aktivieren um es bei jedem PC-Neustart automatisch starten zu lassen.

```
root@pi21:~# systemctl enable auganm17-programm
```

Um alles wirksam zu machen muss man den Raspberry Neustarten

```
root@pi21:~# reboot
```

-----

# Komprimieren

>Die Datenkompression – auch Datenkomprimierung genannt – ist ein Vorgang, bei dem die Menge digitaler Daten verdichtet oder reduziert wird. Dadurch sinkt der benötigte Speicherplatz und die Übertragungszeit der Daten verkürzt sich. In der Nachrichtentechnik wird die Komprimierung von Nachrichten aus einer Quelle durch einen Sender als Quellenkodierung bezeichnet.

>Grundsätzlich wird bei der Datenkompression versucht, redundante Informationen zu entfernen. Dazu werden die Daten in eine Darstellung überführt, mit der sich alle – oder zumindest die meisten – Informationen in kürzerer Form darstellen lassen. Diesen Vorgang übernimmt ein Kodierer und man bezeichnet den Vorgang als Kompression oder Komprimierung. Die Umkehrung bezeichnet man als Dekompression oder Dekomprimierung.

>Man spricht von verlustfreier Kompression, verlustfreier Kodierung oder Redundanzreduktion, wenn aus den komprimierten Daten wieder exakt die Originaldaten gewonnen werden können. Das ist beispielsweise bei der Kompression ausführbarer Programmdateien notwendig. 

**Quelle:** [Wikipedia](https://de.wikipedia.org/wiki/Datenkompression)

### Windows

Bei Windows ist alles verschachtelt und man kann schwer nachvollziehen was, wie, wo, komprimiert worden ist.

### Ubuntu

Bei Ubuntu hingegen gibt es immer eine gleiche vorgangsweise  
```
    gnu-zip  
    tar  
    gzip  
    openssl  
```
