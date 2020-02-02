# Protokoll LA1 / 3AHME (2019/20)
* **Thema:** Rasperry
* **Datum:** 27.01.2020
* **Gefehlt:** ---
* **Erstellt von:** strrim17
* **Protokoll letzte Einheit:** ---

------------------------------------------------------------------------------------------------------------------------

## Inhaltsverzeichnis

1. [Rasperry](#rasperry)
   1. [Vorteile / Nachteile](#vorteile-/-nachteile)
   2. [Schul Programm](#schul-programm)
   3. [SSH Protokoll](#ssh-protokoll)
      1. [Start / Status / Stop Befehle](#start-/-status-/-stop-befehle)
2. [Links](#links)

------------------------------------------------------------------------------------------------------------------------

### Rasperry
Der Raspberry Pi ist ein Einplatinencomputer. Der Rechner enthält ein Ein-Chip-System, kurz gesagt SoC. Die Platine hat das Format einer Kreditkarte. Der im Vergleich zu üblichen Personal Computern sehr einfach aufgebaute Rechner wurde von der Stiftung mit dem Ziel entwickelt, jungen Menschen den Erwerb von Programmier- und Hardware-Kenntnissen zu erleichtern.

Quelle: [https://de.wikipedia.org/wiki/Raspberry_Pi]

#### Vorteile / Nachteile

**Vorteile**
* Ist ein Minicomputer
* Hat eine Kreditkarten Größe
* Bluetooth
* Kabel / Leitungen
* Man kann alles mit ihm machen.

**Nachteil**
* Nicht Echtzeit fähig.
* Kein Windows Unterstützer
* Google Android als Beta für Rasperry Pi

#### Schul Programm
Dies ist unser Schul Programm, welches wir im NANO - Editor geschrieben haben und folgende Funktion hat: Ausgaben verlangsamen bzw. für ein paar Sekunden einen sogenannten Schlafmodus verwenden.

```
#include <stdio.h>
#include <unistd.h>

void delay (int seconds)
{
  double x = 0;
  for(int j = 0; j < seconds; j++)
  {
    for(int i = 0; i < 1000; i++)
    {
      x = x +0.1;
    }
  }
}

int main () {
  int cnt = 0;
    
  for(int i = 0; i < 5000000; i++)
  {
    cnt++;
    printf("cnt=%d\n", cnt);
    sleep(1);
    //delay(1);
  }
  
  return 0;
}
```

------------------------------------------------------------------------------------------------------------------------

#### SSH Protokoll
Secure Shell oder SSH bezeichnet sowohl ein Netzwerkprotokoll als auch entsprechende Programme, mit deren Hilfe man auf eine
sichere Art und Weise eine verschlüsselte Netzwerkverbindung mit einem entfernten Gerät herstellen kann. Häufig wird diese
Methode verwendet, um lokal eine entfernte Kommandozeile verfügbar zu machen, das heißt, auf einer lokalen Konsole werden die
Ausgaben der entfernten Konsole ausgegeben und die lokalen Tastatureingaben werden an den entfernten Rechner gesendet. Genutzt
werden kann dies beispielsweise zur Fernwartung eines in einem entfernten Rechenzentrum stehenden Servers. Die neuere
Protokoll-Version SSH-2 bietet weitere Funktionen wie Datenübertragung per SFTP.

Quelle: [https://de.wikipedia.org/wiki/Secure_Shell#Funktionsweise]

Anmeldung und Schreiben eines Programms im Terminal:

```
schueler@pcxx:~$ ssh pi@10.200.114.223
The authenticity of host '10.200.114.223 (10.200.114.223)' can't be established.
ECDSA key fingerprint is SHA256:ccJbTtnZN73gUp11fgtFKepFqcrZmDLcOyNq32WkN4Q.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '10.200.114.223' (ECDSA) to the list of known hosts.
pi@10.200.114.223's password:
Linux raspberrypi 4.19.75-v7+ #1270 SMP Tue Sep 24 18:45:11 BST 2019 armv7l

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Mon Jan 13 15:21:46 2020 from 10.200.112.67

SSH is enabled and the default password for the 'pi' user has not been changed.
This is a security risk - please login as the 'pi' user and type 'passwd' to set a new password.
```

##### Start / Status / Stop Befehle
**Programm starten**
  ```
  sudo systemctl start programm
  ```
  
**Status anzeigen lassen**
  ```
  sudo systemctl status programm
  ```
  
**Programm stoppen**
  ```
  sudo systemctl stop programm
  ```

------------------------------------------------------------------------------------------------------------------------

### Links
Hier sind alle Links aufgelistet die oben angegeben worden sind:

[Rasperry]: https://de.wikipedia.org/wiki/Raspberry_Pi
[SSH Protokoll]: https://de.wikipedia.org/wiki/Secure_Shell#Funktionsweise
