# E1. Exercici 9. Processos

## Entrega

1. **Expliqueu què fa l'script de python que usarem i quan acabarà l'execució**

Aquet script ho que fa es imprimir cada segon un número fins a 9999, i acabarem l'execució quant prenem CTRL+Z.

2. **Executeu ara en un terminal l'script amb python hyperloop.py. Mostreu el procés amb la comanda: ps -elf | grep 'loop' i l'estat en el que es troba.**

0 S ism5403+  1945  1917  0  80   0 -  6244 core_s 12:46 pts/0    00:00:00 python hyperloop.py

És troba en l'estat de Sleep.

3. **Mentre s'està executant premeu CTRL+C. Si busqueu el proces amb la comanda: ps -elf | grep 'loop', hi és? Expliqueu què ha passat**

No hi és, per què si prenem CTRL+C el proces que se esta executant el mata.

4. **Torneu a executar en un terminal l'script. Mentre s'estigui executant premeu CTRL+Z. En quin estat es troba ara? Mostreu el resultat de la comanda ps**

0 T ism5403+  2009  1917  0  80   0 -  6244 -      12:52 pts/0    00:00:00 python hyperloop.py

Es troba stopped.

5. **Recuperem en primer pla el procés python amb la comanda fg. S'ha seguit executant tota aquesta estona? Expliqueu perquè.**

No, per què estaba adormint. 

6. **Torneu a prémer CTRL+Z amb el procés python funcionant. Ara recuperem-ne l'execució però en segon pla amb la comanda bg. En quin estat es troba ara el procés? Mostreu el resultat de la comanda ps**

0 S ism5403+  2009  1917  0  80   0 -  6244 core_s 12:52 pts/0    00:00:00 python hyperloop.py

Es troba en Sleep.

7. **Ara recuperem-ne l'execució en primer pla amb la comanda fg. S'ha seguit executant tota aquesta estona? Expliqueu perquè i finalitzeu l'execució de l'script definitivament amb CTRL+C.**

Si, per què está en segon pla i seguix funcionant.

Ara executarem un codi c compilat (un executable) que crearà un procés pare i un fill. El procés fill finalitzarà però el procés pare es quedarà esperant. Això provocarà una situació en la qual el procés fill quedarà en estat zombie. El fitxer amb el codi font en llenguatge C el teniu al fitxer zombie.c que, usant el compilador gcc (gcc zombie.c) de C s'ha generat el fitxer binari a.out que executarem amb: bash a.out. Aquest executable finalitzarà al cap de 100 segons, ho heu de tenir en compte a l'hora de realitzar les següents qûestions.

8. **Mentre s'estigui executant comproveu que apareixen dos processos a.out amb la comanda ps -elf | grep 'a.out'. Mostreu el resultat de la comanda i indiqueu en quin estat es troben**

0 S ism5403+  2438  2204  0  80   0 -  1033 hrtime 13:10 pts/2    00:00:00 ./a.out
1 Z ism5403+  2439  2438  0  80   0 -     0 -      13:10 pts/2    00:00:00 [a.out] <defunct>
0 S ism5403+  2475  2442  0  80   0 -  2677 -      13:11 pts/1    00:00:00 grep --color=auto a.out

Es troba en estat zombie.

9. **Quin dels dos processos a.out que surten a la pregunta anterior és el pare i quin el fill? Com ho heu deduît?**

El proces pare és el 2438 i el proces fill és el 2439. Ho he deduït per què el proces pare esta en sleep i el fill está en zombie.

10. **En una finestra de terminal inicieu una descàrrega de un dels dvd iso de debian i realitzeu les següents operacions en una altra finestra. Poseu aquí les ordres que executeu.**

- Ordre per iniciar la descàrrega i estat del procés de descàrrega: wget https://cdimage.debian.org/debian-cd/current/amd64/iso-dvd/debian-9.6.0-amd64-DVD-3.iso ps -elf

- Ordre per veure l'estat de la descàrrega: ps -elf | grep wget 

- Combinació de tecles per aturar la descàrrega i estat del procés de descàrrega: CTRL + Z ps -elf 

0 T ism5403+  2772  2745 14  80   0 - 20471 -      13:32 pts/1    00:00:09 wget https://cdimage.debian.org/debian-cd/current/amd64/iso-dvd/debian-9.6.0-amd64-DVD-3.iso

- Ordre per recuperar l'execució de la descàrrega en segon pla i estat del procés de descàrrega: bg ps -elf 

0 S ism5403+  2772  2745  8  80   0 - 20471 core_s 13:32 pts/1    00:00:10 wget https://cdimage.debian.org/debian-cd/current/amd64/iso-dvd/debian-9.6.0-amd64-DVD-3.iso

- Ordre per recuperar l'execució de la descàrrega en primer pla i estat del procés de descàrrega: fg ps -elf

0 S ism5403+  2772  2745  9  80   0 - 20471 core_s 13:32 pts/1    00:00:14 wget https://cdimage.debian.org/debian-cd/current/amd64/iso-dvd/debian-9.6.0-amd64-DVD-3.iso
