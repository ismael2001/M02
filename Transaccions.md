**1. Quin/s paquet/s dels repositoris del sistema operatiu cal instal.lar i per a què serveixen?**

- sudo dnf install python3-tkinter -y

**2. Quin/s paquet/s de llibreries de python s'han d'instal.lar i per a què serveixen?**

- sudo dnf install pip3 install requests numpy matplotlib

Numpy : ens permetrà llegir les dades del fitxer i desar-les en un format que ens permeti posteriorment graficar-les

Matplotlib : permet fer gràfiques i gestionar-ne els paràmetres a partir de les dades llegides

**3. Expliqueu què es fa en cada part de la transacció del nostre programa python:**

- **_ENTRADA_** : curl "https://www.bicing.cat/current-bikes-in-use.json"

- **_EMMAGATZEMATGE_** : dades = numpy.genfromtxt('databicing.csv',delimiter=',', skip_header=1, usecols=(3)) **(es guarden les dades en un arxiu)**

- **_PROCESSAMENT_** : databicing.csv	**(es processen les dades)**

- **_SORTIDA_** : plt.plot(dades)    	
		  plt.title('Bicing')    
		  plt.ylabel('Bicis')  
		  plt.xlabel('Temps')  


**4. Què hauríem de canviar al codi per tal que en comptes de mostrar les bicicletes totals en ús ens mostrés només les bicicletes elèctriques en ús?**

- la columna , s'ha d'escollir que només agafi les dades de les bicicletes elèctriques en us.

**5. Canvieu ara els següents paràmetres del nostre programa python i copieu aquí el programa sencer una vegada modificat i comprovat que fa el que ha de fer. També copieu aquí les dades que s'han emmagatzemat al fitxer:**

- Feu que faci 30 iteracions en comptes de 10: 

*canviant l'iteració en compte de 10 , posem 30 , però faria 31 repeticions , llavors a l'iteració tenim un "<=30 , major o igual que 30" la cual cosa faria 31 repeticions , llavors treiem l'igual i faria 30 repeticions.*

- Canvieu el títol de la gràfica de 'Bicing' pel vostre nom i cognoms:

*plt.title('Samuel Chiriboga Hidalgo')*


**DADES EMMAGATZEMADES** : 

error,bikesInUsage,electricalBikesInUsage,mechanicalBikesInUsage,dateTime
0,472,2,470,2018-10-22 12:48:15  
0,472,2,470,2018-10-22 12:48:16  
0,473,2,471,2018-10-22 12:48:18  
0,472,2,470,2018-10-22 12:48:19  
0,474,2,472,2018-10-22 12:48:20  
0,475,2,473,2018-10-22 12:48:22  
0,476,2,474,2018-10-22 12:48:23  
0,475,2,473,2018-10-22 12:48:25  
0,473,2,471,2018-10-22 12:48:26  
0,474,2,472,2018-10-22 12:48:28  
0,475,2,473,2018-10-22 12:48:29  
0,475,2,473,2018-10-22 12:48:31  
0,474,2,472,2018-10-22 12:48:32  
0,475,2,473,2018-10-22 12:48:34  
0,473,2,471,2018-10-22 12:48:35  
0,474,2,472,2018-10-22 12:48:37  
0,472,2,470,2018-10-22 12:48:38  
0,471,2,469,2018-10-22 12:48:40  
0,470,2,468,2018-10-22 12:48:41  
0,468,2,466,2018-10-22 12:48:43  
0,468,2,466,2018-10-22 12:48:44  
0,469,2,467,2018-10-22 12:48:46  
0,469,2,467,2018-10-22 12:48:47  
0,469,2,467,2018-10-22 12:48:49  
0,471,2,469,2018-10-22 12:48:50  
0,471,2,469,2018-10-22 12:48:51  
0,472,2,470,2018-10-22 12:48:53  
0,473,2,471,2018-10-22 12:48:54  
0,473,2,471,2018-10-22 12:48:56  
0,474,2,472,2018-10-22 12:48:57+  


**CODI FINAL** : 


 	Autor: Ismael Díaz Martínez 				 
 	Llicència: AGPLv2                                                          
 	DESCRIPCIO                                                                 
 	 	Es conectarà 10 vegadas a la api json de bicing en intervals d'un segon 
 	 	i posteriorment mostrarà l'evolució en una gràfica                       
	 INSTALL LIBRARIES:                                                       
 		sudo dnf install python3-tkinter -y                                      
   		sudo pip3 install requests numpy matplotlib                              
	RUN:									      
 	 	python3 bikesInUse.py                                                    



**Farem ús de llibreries que contenen funcions que ens seran útils**  
	 
**La llibreria requests ens permetrà conectar amb direccions URL**  
	import requests
	
**La llibreria time té la funció d'esperar uns segons**  
	import time
	
**La llibreria csv ens permet desar dades en format CSV compatible amb fulls de càlcul**  
	import csv
	
**databicing serà una variable de tipus llista. A la llista hi anirem desant les dades que ens retorni el web de bicing.**  
	databicing=[]
	
**iteració serà una variable entera que ens servirà per anar comptant quantes vegades fem el bucle. Inicialment 0.**  
	iteracio=0
	
**El bucle while es repetirà mentre iteracio sigui menor que 10. Per tant anirà de 0 a 10. Dins el bucle l'incrementarem amb iteracio=iteració+1.**  
	
**La funció sleep de la llibreria time esperarà 1 segon, sense fer res.**  
	
**I a la primera linia afegirem el resultat que ens doni el web amb el requests.get en format json a la llista databicing que hem creat abans.**  
	
**Al print mostrarem en quin número de petició estem. Fixeu-vos que convertim el valor enter en un string de caràcters per tal de mostrar-lo.**    
	while iteracio < 30:  
		databicing.append(requests.get("https://www.bicing.cat/current-bikes-in-use.json").json())  
		time.sleep(1)  
		iteracio=iteracio+1  
		print("Petició Nº:"+str(iteracio))  
		print("  Dades: "+str(databicing[iteracio-1]))  
	
**Ara ja tenim les dades a la memòria de l'ordinador, dins la variable databicing que és una llista. Per accedir a cada petició emmagatzemada a aquesta llista ho farem amb l'índex, en aquest cas la primera és la 0 , d'aquesta primera petició n'agafarem els títols, que són les claus (keys)**  
	titols = databicing[0].keys()

**I aquí el que fem és obrir un fitxer databicing.csv en mode escriptura i anar-hi desant les dades en format csv**  
	print(databicing)  
	with open('databicing.csv', 'w') as fitxer:  
    	punter = csv.DictWriter(fitxer, titols)  
    	punter.writeheader()  
    	punter.writerows(databicing)  

**Hem fet un seguit de peticions al web de bicing mitjançant la tarja de xarxa i els protocols de xarxa que ens proporciona el sistema operatiu.**  

**Hem anat dient-li al sistema operatiu que desi aquestes dades que rebem a la memòria volàtil de l'ordinador (RAM) dins la variable databicing ,i finalment li hem dit al sistema operatiu que desi aquestes dades en un fitxer anomenat databicing.**  
	
**Ara passarem a llegir les dades i fer-ne una gràfica.**  
	
**El primer que farem és importar les llibreries que ens facilitaran les funcions per a fer-ho.**  

**La lliberia numpy ens permetrà llegir les dades del fitxer i desar-les en un format que ens permeti posteriorment graficar-les**  
	import numpy
	
**La llibreria matplotlib permet fer gràfiques i gestionar-ne els paràmetres a partir de les dades llegides del fitxer databicing.csv**  
	~ import matplotlib  
	from matplotlib import pyplot as plt  
	
**Llegim les dades del fitxer**  
	dades = numpy.genfromtxt('databicing.csv',delimiter=',', skip_header=1, usecols=(3))  
	
**Dibuixem les dades en memòria i posem títols a la gràfica**  
		plt.plot(dades)  
		plt.title('Ismael Díaz Martínez')  
		plt.ylabel('Bicis')  
		plt.xlabel('Temps')  
	
**Generem una finestra on mostrar la gràfica que tenim en memòria.**  
		plt.show()
	
