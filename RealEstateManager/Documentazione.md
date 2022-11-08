# Documentazione Real Estate Manager

## **Sommario**

1. Introduzione
2. Requisiti funzionali
3. Interfaccia utente
4. Meccaniche principali
5. Sviluppo
6. Conclusioni

<br>

***
## **Introduzione**
<br>
Lo scopo di questo documento e' quello di spiegare in maniera tecnica le funzionalita' del programma **Real Estate Manager**.

Tale software e' stato implementato da : 

- **Marko Milunovic** (Matricola: 725836)

Il software in questione e' stato implementato al fine di organizzare la vendita delle case e di gestire le componenti:
1. Case(insieme di tutte le case sia in vendita che non)
2. Citta(insieme di tutte citta')
3. Zone(insieme di tutte le zone)

Inoltre si occupa di fare una stima del prezzo spettante di una casa in vendita (attraverso l'uso di un classificatore) e di calcolare la probabilita' di poter vendere la casa in tempo breve in base ad alcune informazioni.

<br>

***
## **Requisiti funzionali**
<br>
Il programma per essere avviato necessita di alcuni pacchetti, installabili attraverso i seguenti comandi:

1. 'pybbn' -> ```pip install pybbn``` utile per la predizione;
2. 'pandas' -> ```pip install pandas``` utile per il classificatore;
3. 'tabulate' -> ```pip install tabulate``` utile per il layout delle tabele;
4. 'sklearn.tree' -> ```pip install scikit-learn``` utile per il classificatore; 
5. 'pyswip' -> ```pip install pyswip``` per la base di conoscenza in Prolog;
6.  bisognerà anche installare Swi-Prolog:
    - andare nel sito ufficiale;
    - recarsi nella sezione di download;
    - selezionare ```stable release```, scaricare la versione adatta al proprio sistema operativo;
    - successivamente installare il programma sulla propria macchina ```Add swipl to the system PATH for current user```.


<br>

***
## **Interfaccia utente**
<br>
Una volta avviato il programma vera' visualizzato un messaggio di benvenuto:

<br>
<center>

```Benvenuto nel portale RealEstate Manager.```

```Grazie al nostro aiuto potrai consultare numerose informazioni riguardanti la vendita delle case.```
</center>
<br>
E inoltre comparira' un messaggio di default a ogni interazione:

<br>
<center>

```Bisogno di aiuto? Per visualizzare la lista dei comandi digita: -1 ```

</center>
<br>
Al termine dell'esecuzione comparira' tale messaggio e l'applicazione verra' chiusa:

<br>
<center>

```Grazie per aver utilizzato il nostro servizio. Arrivederci!```

</center>

<br>
All'interno del programma inoltre vengono effettuati dei controlli riguardo l'input dell'utente. Nel caso in cui dovesse inserire un comando o una parola errata apparira' un messaggio di errore (es. se il nome della citta inserita contiene i numeri apparira' il messaggio di errore: "Valore inserito non valido. Inserire solo lettere!").

<br>

***

## **Meccaniche principali**
<br>

In questo software si e' scelto di utilizzare:

1. Una **base di conoscenza**, all'interno del quale sono presenti le liste delle citta', delle zone e delle case, scritta in Prolog.

2. Un **classificatore** in grado di restituire l'ipotetico prezzo di una casa in vendita in base al numero di metri quadri della casa, al numero dei locali e al piano.

<br>
<br>
Inoltre e' stato utilizzato il Linear Kernel Cross Validation per la precisione del classificatore poiche' i dati a disposizione erano pochi. 

E' stato utilizzato un file CSV all'interno del quale ci saranno le informazioni su:
* **m^2**;
* **locali**;
* **piano**.



<br>

Rispettivamente:
* Nel campo *metri quadri* e' presente un numero che identifica il numero di metri quadrati della casa, i valori vanno da 20 a 400;
* Nel campo locali e' presente un numero che identifica il numero di locali della casa, i valori vanno da 1 a 10;
* Nel campo piano e' presente un numero che identifica il piano su cui si trova la casa, i valori vanno da 1 a 10.
* Per quanto riguarda il prezzo verra' calcolato un possibile prezzo spettante.

3. Per predire la probabilita' di vendere la casa e' stata usata una  **rete bayesiana**. Utile per avere una stima generale 
quando e' presente un certo grado di incertezza. A tal fine l'utente dovra' rispondere ad alcune domande.

<br>

In base alla percentuale restituita:
*  ```< 30%``` : probabilita' di vendita ```bassa```;
*  ```< 45%``` : probabilita' di vendita ```medio-bassa```;
*  ```< 60%``` : probabilita' di vendita ```media```;
*  ```< 80%``` : probabilita' di vendita ```medio-alta```;
*  ```>= 80%``` : probabilita' di vendita ```alta```.

<br>

Ogni risposta e' pesata differentemente e queste percentuali sono determinate da:

* **Stato Casa**: in quale stato si trova la casa;  
* **Arredamento**: se la casa e' arredata o meno;
* **Condizione**: contiene ```Stato casa``` e ```Arredamento```;
* **Prossimita'**: se la casa si trova in prossimita' dei servizi pubblici;
* **Locazione**: se la casa si trova in centro o in periferia;
* **Facilita' Spostamento**: contiene ```Prossimita'``` e ```Locazione```;
* **Qualita' Casa**: contiene ```Condizione``` e ```Facilita' Spostamento```;
* **Presenza Balcone**: se la casa possiede un balcone;
* **Posto Auto**: se la casa dispone di un posto per lasciare la macchina(es. garage);
* **Caratteristiche**: contiene ```Presenza balcone``` e ```Posto auto```;
* **Previsione vendita**: contiene ```Qualita'casa``` e ```Caratteristiche```;

<br>

***

## **Sviluppo**

<br>

Il progetto e' stato realizzato utilizzando la piattaforma gitHub e come ambiente di lavoro Eclipse. I linguaggi che sono stati utilizzati sono: python, prolog.

<br>

***

<br>

<center>

**[REAL ESTATE MANAGER]()**

</center>
