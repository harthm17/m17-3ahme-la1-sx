# Protokoll LA1/SX 3AHME (2019/20)

* **Thema:** Linux Scripting
* **Datum:** 20.04.2020
* **Gefehlt:** -
* **Erstellt von:** Marcher Simon
* **Protokoll letzte Einheit:** [Protokoll 30.03.2020](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/marsim17/protokolle/protokoll-4-marsim17-2020-30-03.md)
---------
## Inhaltsverzeichnis
[Begriffserklärung](#begriffserklärung)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Deamons in Linux](#deamons-in-linux)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Daemons in Java](#deamons-in-java)  
[Erstellen eines eigenen Deamons](#erstellen-eines-eigenen-deamons)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Programm erstellen](#programm-erstellen)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[systemd Service erstellen](#systemd-service-erstellen)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Service ausführen und überwachen](#service-ausführen-und-überwachen)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Autostart](#autostart)

## Begriffserklärung
### Deamons in Linux
Unter Linux werden Prozesse vom Kernel in 3 Unterkategorien geteilt: Interaktive Prozesse, Bash-Prozesse und [Deamons](https://en.wikipedia.org/wiki/Daemon_(computing)#Unix-like_systems). Deamons sind Hintergrundprozesse, die von anderen Prozessen benötigt werden. Sie werden automatisch beim Booten gestartet und werden erst beim Herunterfahren wieder beendet.

### Deamons in Java
Ein Deamon Thread in Java ist ein spezieller Thread, der die JVM nicht daran hindert zu schließen. Auf der anderen Seite gibt es die High-Priority Threads, die zuerst schließen müssen bevor die JVM es tun kann. Alle Threads innerhalb der main() Methode sind zum Beispiel High-Priority Threads. Ein Beispiel eines Deamons-Threads ist der Garbage Collector. 
