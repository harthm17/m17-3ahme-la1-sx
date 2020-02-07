 # Protokoll Labor/SX 3AHME (2019/20) 


* **Thema** : Raspberry PI 
* **Datum** : 03.02.2020 
* **Gruppe** : 4 
* **Protokollverfasser** : Christoph Sebernegg 
* **Protokoll letzte Einheit** : [4.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/sebchm17/sebchm17/protokolle/protokoll_2020-01-27_sebchm17.md) 

-------------------------------------------------------------------------------------------------------------------------------- 

## Inhaltsverzeichnis 

1.  [Einsteigen auf dem Raspberry](#einsteigen-auf-dem-raspberry)
1.  [Portnummern](#portnummern)
1.  [Richard Stallman](#richard-stallman)
1.  [Über SSH einsteigen](#über-ssh-einsteigen) 
1.  [C-Programm erstellen, compelieren und ausführen](#c-programm-erstellen-compelieren-und-ausführen) 
1.  [Autostartprogramm erstellen](#autostartprogramm-erstellen) 

---------------------------------------------------------------------------------------------------------------------------------

    sebchm@pi16:~/programm $ nano main.c 

```C  
      #include  <stdio.h>
      #include  <unistd.h>
      
      int main()
      {
        int cnt=0;
        
        for(int i=0; i<10; i++)
        {
          cnt++;
          printf("cnt=%d\n", cnt);
          FILE *f;
          f=fopen("/var/log/programm.log","a");
          if(f!= NULL){
          fprintf(f, "cnt=%d\n",cnt);
          fclose(f);
          }
          sleep(1); 
         
         }
         return 0;
```  

``` bash
     /var/log/programm.log
     {
       rotate 4
       weekly
       missingok
       notifempty
     }
```




















