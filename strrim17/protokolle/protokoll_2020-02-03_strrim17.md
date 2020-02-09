# Protokoll LA1 / 3AHME (2019/20)
* **Thema:** Autostart
* **Datum:** 03.02.2020
* **Gefehlt:** ---
* **Erstellt von:** strrim17
* **Protokoll letzte Einheit:** [Raspberry](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/edit/strrim17/strrim17/protokolle/protokoll_2020-01-27_strrim17.md)

------------------------------------------------------------------------------------------------------------------------

## Inhaltsverzeichnis

1. [Start / Status / Stop - Befehle](#start-/-status-/-stop---befehle)
2. [Tail / Head - Befehle](#tail-/-head---befehle)
3. [Autostart](#autostart)
4. [Passwort erstellen](#passwort-erstellen)
5. [Programm installieren](#programm-installieren)
6. [Links](#links)

------------------------------------------------------------------------------------------------------------------------

## Start / Status / Stop - Befehle
**Programm starten**
Befehl zum starten des Programms.

  ```
  sudo systemctl start programm
  ```
  
**Status anzeigen lassen**
Befehl zum Abfragen des Programms, ob es läuft bzw. funktioniert oder nicht.

  ```
  sudo systemctl status programm
  ```
  
**Programm stoppen**
Befehl zum stoppen des Programms.

  ```
  sudo systemctl stop programm
  ```
## Tail / Head - Befehle
In den Folgenden beiden Befehlen wird angegeben, dass in unserem Schul programm folgende Zeilen ausgegeben werden.

**Zeilen am Anfang ausgeben**
Befehl zum Ausgeben der ersten Zeilen des Programms bzw. der Datei.

  ```
  head -f /var/log/programm.log
  ```
  
Beispiel:
  
  ```
  pi@raspberrypi:~/programm $ head -f /var/log/programm.log
  cnt=1
  cnt=2
  cnt=3
  cnt=4
  cnt=5
  ```

**Zeilen am Ende ausgeben**
Befehl zum Ausgeben der letzten Zeilen des Programms bzw. der Datei.

  ```
  tail -f /var/log/programm.log
  ```
  
Beispiel:
  
  ```
  pi@raspberrypi:~/programm $ tail -f /var/log/programm.log
  cnt=56
  cnt=57
  cnt=58
  cnt=59
  cnt=60
  ```

## Autostart
Beim Autostart ist es wohl klar, dass sich Programm selbst starten sollte, anstatt das man es extra starten muss.
Das bedeutet, dass das Programm sich automatisch einschaltet bzw. startet, sobald das Gerät eingeschaltet ist.

  ```
  pi@raspberrypi:~/programm $ systemctl enable programm
  ```
  
In meinem Fall funktionierte der Autostart nicht. Doch dafür gibt es eine andere Möglichkeit.
  
  ```
  pi@raspberrypi:~/programm $ systemctl enable programm
  ==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-unit-files ===
  Authentication is required to manage system service or unit files.
  Authenticating as: root
  Password:
  polkit-agent-helper-1: pam_authenticate failed: Authentication failure
  ==== AUTHENTICATION FAILED ===
  Failed to enable unit: Access denied
  ```
  
Falls der Autostart nicht funktioniert, muss man in den Administrator wechseln und dort den Befehl ausführen.
  
  ```
  root@raspberrypi:~# systemctl enable programm
  Created symlink /etc/systemd/system/multi-user.target.wants/programm.service → /etc/systemd/system/programm.service.
  ```

## Passwort erstellen
Um sicher arbeiten zu können, benutzt man ein asymetrisches Schlüsselpaar:"Öffentlicher & Privater - Schlüssel"
Befehle zum erstellen eines Passwortes.

**Schlüsseldateien** 
  ```
  ll.ssh
  ```
  
**Schlüsselpaar erstellen**
  ```
  ssh-keygen
  ```
  
**Öffentlicher Schlüssel**
  ```
  cat .ssh/id-rsa.pub
  ```
  
**Privater Schlüssel** 
  ```
  cat .ssh/id-rsa
  ```

Dies ist ein in der Schule gefertigter Schlüssel, welcher von jedem selbst angelegt wurde.

  ```
  schueler@pcxx:~$ ll .ssh
  insgesamt 16
  drwx------  2 schueler schueler 4096 Feb  3 14:16 ./
  drwxr-xr-x 26 schueler schueler 4096 Feb  3 14:13 ../
  -rwx------  1 schueler schueler  783 Nov  7  2018 authorized_keys*
  -rw-r--r--  1 schueler schueler  222 Feb  3 14:16 known_hosts
  schueler@pcxx:~$ ssh-keygen
  Generating public/private rsa key pair.
  Enter file in which to save the key (/home/schueler/.ssh/id_rsa):
  Enter passphrase (empty for no passphrase):
  Enter same passphrase again:
  Your identification has been saved in /home/schueler/.ssh/id_rsa.
  Your public key has been saved in /home/schueler/.ssh/id_rsa.pub.
  The key fingerprint is:
  SHA256:xnsV3Yhk2wxVHO3S4/OE/4KxD17Vw/9WQm6qrwvrpFk schueler@pcxx
  The key's randomart image is:
  +---[RSA 2048]----+
  |            +..++|
  |           o B oo|
  |            + =o.|
  |       .     .+.+|
  |        S   .o.=+|
  |       . . .. =+=|
  |        E . .*.+=|
  |       = + .+o. =|
  |      o.o +=o..o+|
  +----[SHA256]-----+
  schueler@pcxx:~$ ll .ssh
  insgesamt 24
  drwx------  2 schueler schueler 4096 Feb  3 16:02 ./
  drwxr-xr-x 26 schueler schueler 4096 Feb  3 14:13 ../
  -rwx------  1 schueler schueler  783 Nov  7  2018 authorized_keys*
  -rw-------  1 schueler schueler 1679 Feb  3 16:02 id_rsa
  -rw-r--r--  1 schueler schueler  395 Feb  3 16:02 id_rsa.pub
  -rw-r--r--  1 schueler schueler  222 Feb  3 14:16 known_hosts
  schueler@pcxx:~$ cat .ssh/id_rsa.pub
  ssh-rsa   AAAAB3NzaC1yc2EAAAADAQABAAABAQC/Awf8uN/RVjj53UMg+JQt3CqLWv7EwE1Mu56oqZ/45sO7Dr7Ouewk90vB6HF4wazFSC+CTmOrVD7g1uoipRmGdK8Mptuw1G//rIaksMFu Lu/NnxY15+WgSH5Yry7lZpFp6Hc9zWz/gAP7S08x8dyghwlyj1cy0rm6wWYh4tRAGtnzoElofajvMZX9qxcRdJxTGd+kEp57o5d9wjkYMaHYLvyEEB5vGdpEiwq2/55VATste9m1  Wtb90cM5Oc/reVr9l3CateEr/cpQJ7PxpRXGCPZFv72mACadDxnHgQiX93PsvhIayD83j+HWt8J052XUog5D9x0FqPhlpGQXmsi3 schueler@pcxx
  schueler@pcxx:~$ cat .ssh/id_rsa
  -----BEGIN RSA PRIVATE KEY-----
  MIIEpAIBAAKCAQEAvwMH/Ljf0VY4+d1DIPiULdwqi1r+xMBNTLueqKmf+ObDuw6+
  zrnsJPdLwehxeMGsxUgvgk5jq1Q+4NbqIqUZhnSvDKbbsNRv/6yGpLDBbi7vzZ8W
  NefloEh+WK8u5WaRaeh3Pc1s/4AD+0tPMfHcoIcJco9XMtK5usFmIeLUQBrZ86BJ
  aH2o7zGV/asXEXScUxnfpBKee6OXfcI5GDGh2C78hBAebxnaRIsKtv+eVQE7LXvZ
  tVrW/dHDOTnP63la/ZdwmrXhK/3KUCez8aUVxgj2Rb+9pgAmnQ8Zx4EIl/dz7L4S
  Gsg/N4/h1rfCdOdl1KIOQ/cdBaj4ZaRkF5rItwIDAQABAoIBAGa7iqAyDq7YYOyC
  RIiHKatAruEkn8HSa8DJaBvun0uPUdZZp+YnuQpotyYjjmQURogUuviqkJClTuw+
  qs7XXVMjjsKPO7lviI1KjWAmcOKB/BfraFa10prSYqHwFpjrAWqkzP1Ab0872uhd
  KMsD+lWcS0iCL7P2Ak6flf7DsMSIvL3UJUU47VKsZse++X2bVPYsSQyukrVBX2Kl
  Dci+prDKHPfgeX5IyOeDvqnDW31hYHciZq2YCTPthvfiYnD3y59Vwj8yNq7eMVCu
  0b3r00KZJa1kYGGOB409sdgsRKqEak+YEn2XZ3HGn5gA7SPDKjdE4HjDlwn6BiIk
  rewOzoECgYEA+1zxR9p+g3m6HeXkS8Sb4RCAq1YLsf6AZoyscBY4o6VnlEElMOq/
  JegkI0lElx9NKxScwOuBiECNqdI8P/kzlaS2P5zewoshSvB5zczrRfSGYyREEuYC
  hY9pux34KeuEpnlQfUi2W8HweQNRZvYtd/8be4HfmO5QO0pkpDVcLd0CgYEAwokU
  x4AQrMDt7gLRXB3dXG0BGO5zdr7DhUcLcJdwOTwRy3x1M7bFVCQRGYf6cCM/35Pp
  dHlxuCquskn8ykHMejoTQ6oj43jZ8JDVRmKQjOVKgPSOCyg9AtDy4qDy/PQygYov
  3HphGpcak7cof7eMZCvfafy++BTmCxuio8G7GaMCgYEAvCS/PMcgdwx/8K0IimXp
  Pzb4+EX5jwst1JRq5aLcVjESLHfufITY+mid1AOdYXg+bIaLJiOg2vlmj7wa+M9w
  ewvEliy21+sHym3g3dgKKlxy0nZstbCQJqRHwZUXEVmF+o1HX98zD89ETW/cWDLf
  qbe7PGDjmjaWuypd1kNScckCgYA7qpnh+siig+Y2O00FiO9tOs28XN6zTB1iEoFS
  vlAgbekzVXAJNYTeotVP1GIe5ODhbVeMbvdPOmAstP7A9l+GGavw9A1f5qBJ5dJU
  bUTSwj0QwnGSwHu+EmJ82krNBQU8sCqv4CVKZ5AyQFo+mgiIbOBwfKICKz7Hp2lB
  +titKwKBgQCdoyk+/WvlWksRpvLl12NN7hhx8uq9XlCBVxZBXUevmTQDLOTrqpOX
  X2d2sruqJo2W1fR9kuybbr6ZcoVU2rsW9YUDdluCXLhAQcJMsCze3zOMwmPBea6d
  sGYzcZnMJFdAQxob7Xgd2KJHzlk7p4oTBCj0rkiyicqA7kLA5SQIdg==
  -----END RSA PRIVATE KEY-----
  schueler@pcxx:~$ cat .ssh/id_rsa.pub
  ssh-rsa  AAAAB3NzaC1yc2EAAAADAQABAAABAQC/Awf8uN/RVjj53UMg+JQt3CqLWv7EwE1Mu56oqZ/45sO7Dr7Ouewk90vB6HF4wazFSC+CTmOrVD7g1uoipRmGdK8Mptuw1G//rIaksMFu  Lu/NnxY15+WgSH5Yry7lZpFp6Hc9zWz/gAP7S08x8dyghwlyj1cy0rm6wWYh4tRAGtnzoElofajvMZX9qxcRdJxTGd+kEp57o5d9wjkYMaHYLvyEEB5vGdpEiwq2/55VATste9m1  Wtb90cM5Oc/reVr9l3CateEr/cpQJ7PxpRXGCPZFv72mACadDxnHgQiX93PsvhIayD83j+HWt8J052XUog5D9x0FqPhlpGQXmsi3 schueler@pcxx
  schueler@pcxx:~$ ll .ssh
  insgesamt 24
  drwx------  2 schueler schueler 4096 Feb  3 16:02 ./
  drwxr-xr-x 26 schueler schueler 4096 Feb  3 14:13 ../
  -rwx------  1 schueler schueler  783 Nov  7  2018 authorized_keys*
  -rw-------  1 schueler schueler 1679 Feb  3 16:02 id_rsa
  -rw-r--r--  1 schueler schueler  395 Feb  3 16:02 id_rsa.pub
  -rw-r--r--  1 schueler schueler  222 Feb  3 14:16 known_hosts
  schueler@pcxx:~$ ssh-copy-id pi@10.200.114.223
  /usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
  /usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
  pi@10.200.114.223's password:

  Number of key(s) added: 1

  Now try logging into the machine, with:   "ssh 'pi@10.200.114.223'"
  and check to make sure that only the key(s) you wanted were added.

  schueler@pcxx:~$ rsync root@10.200.114.223/home /tmp
  rsync: change_dir "/home/schueler//root@10.200.114.223" failed: No such file or directory (2)
  rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1196) [sender=3.1.2]
  schueler@pcxx:~$
  ```


## Programm installieren
Befehle zum installieren eines Programmes auf einem Raspberry.

  ```
  root@raspberrypi:~# apt update
  ```
  
  ```
  root@raspberrypi:~# apt install
  ```
  
Schul Programm bzw. Beispiel:
  
  ```
  root@raspberrypi:~# apt update
  Get:1 http://archive.raspberrypi.org/debian buster InRelease [25.2 kB]
  Get:2 http://raspbian.raspberrypi.org/raspbian buster InRelease [15.0 kB]
  Get:3 http://raspbian.raspberrypi.org/raspbian buster/main armhf Packages [13.0 MB]
  Get:4 http://archive.raspberrypi.org/debian buster/main armhf Packages [276 kB]
  Fetched 13.3 MB in 16s (848 kB/s)                                          
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  67 packages can be upgraded. Run 'apt list --upgradable' to see them.
  root@raspberrypi:~# apt install
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  0 upgraded, 0 newly installed, 0 to remove and 67 not upgraded.
  ```

## Links
Hier sind alle Links aufgelistet die oben angegeben worden sind:

---
