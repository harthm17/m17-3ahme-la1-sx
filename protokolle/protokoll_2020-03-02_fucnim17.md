
Nickname erstellen:

nano .ssh/config
  Host pi16-root
   Hostname 10.200.114.222
   User root 
   Host pi16-root
   Hostname 10.200.114.222
   User root 
   
   
 Programm erstellen:
 
fucnim17@pi22:~ $ mkdir programm
fucnim17@pi22:~ $ ls
programm
fucnim17@pi22:~ $ cd programm/
fucnim17@pi22:~/programm $ nano main.c


Textdatei in Programm umwandeln:
mit Compiler (z.B. GNU Compiler) --> GNU Project
fucnim17@pi22:~/programm $ gcc main.c

Ausführen: fucnim17@pi22:~/programm $ ./a.out

Ausgabe in einer Datei:

ls -al /var/log
sudo touch /var/log/programm.log
sudo chmod 666/var/log/programm.log
ls -al /var/log/programm.log
gcc main.c
./a.out

Datei "überwachen":
fucnim17@pi22:~ $ watch ls -l /var/log/programm.log

oder

fucnim17@pi22:~ $ tail -f /var/log/programm.log


Logrotate











