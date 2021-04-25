---
title: "Leggere tabelle sottoforma di DataFrame"
teaching: 10
exercises: 10
questions:
- "Come si possono leggere i dati di una tabella?"
objectives:
- "Importare la libreria Pandas."
- "Usare Pandas per caricare un semplice dataset in formato CSV."
- "Leggere le informazioni di base relative a un DataFrame di Pandas."
keypoints:
- "Usare la libreria Pandas per studiare le statistiche di base di una tabella di dati."
- "Usre `index_col` per specificare che i valori di una colonna devono essere usati come titoli delle righe."
- "Usare `DataFrame.info` per saperne di più su un dataframe."
- "La variabile `DataFrame.columns` contiene le informazioni relative alle colonne del dataframe."
- "Usare `DataFrame.T` per trasporre un dataframe."
- "Usare `DataFrame.describe` per calcolare le statistiche riassuntive di un insieme di dati."
---
## Usare la libreria Pandas per studiare le statistiche di base di una tabella di dati.

*   Pandas è una libreria di Python, diffusamente usata per la statistica, in particolare su dati tabulari.
*   Prende in prestito molte caratteristiche dei dataframe del linguaggio di programmazione R.
    *   Una tabella bidimensionale le cui colonne hanno nomi assegnati
        e, potenzialmente, tipi di dati diversi.
*   La libreria si importa usando `import pandas as pd`. L'alias `pd` è quello usato più comunemente per Pandas.
*   Si può leggere un file di dati CSV (Comma-Separated Values, valori separati da virgole) usando `pd.read_csv`.
    *   L'argomento della funzione è il nome del file da leggere.
    *   Per tenere in memoria i dati letti dal file, si assegna il risultato a una variabile.

~~~
import pandas as pd

data = pd.read_csv('data/gapminder_gdp_oceania.csv')
print(data)
~~~
{: .language-python}
~~~
       country  gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  \n0    Australia     10039.59564     10949.64959     12217.22686
1  New Zealand     10556.57566     12247.39532     13175.67800


   gdpPercap_1967  gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  \n0     14526.12465     16788.62948     18334.19751     19477.00928
1     14463.91893     16046.03728     16233.71770     17632.41040


   gdpPercap_1987  gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  \n0     21888.88903     23424.76683     26997.93657     30687.75473
1     19007.19129     18363.32494     21050.41377     23189.80135


   gdpPercap_2007
0     34435.36744
1     25185.00911
~~~
{: .output}

*   Le colonne di un dataframe sono le variabili misurate, mentre le righe sono le singole misurazioni.
*   Pandas usa la barra rovesciata `\` per indicare le linee di testo che sono state mandate a capo perché troppo larghe per lo schermo.

> ## File non trovato
>
> Le nostre lezioni hanno i file di dati salvati in una sottocartella `data`,
> ragion per cui il percorso del file è `data/gapminder_gdp_oceania.csv`.
> Se ti dimentichi di mettere `data/`, o se lo metti, ma la tua copia
> del file è stata salvata altrove, otterrai un
> [runtime error]({{ page.root }}/04-built-in/#runtime-error)
> che finisce con una frase come questa:
>
> ~~~
> OSError: File b'gapminder_gdp_oceania.csv' does not exist
> ~~~
> {: .error}
{: .callout}

## Usare `index_col` per specificare che i valori di una colonna devono essere usati come titoli delle righe.

*   I titoli  delle righe sono numeri (0 e 1, in questo caso).
*   Vogliamo però indicizzare in base al paese.
*   Per fare ciò, passa il nome della colonna alla funzione `read_csv` attraverso il suo parametro `index_col`.

~~~
data = pd.read_csv('data/gapminder_gdp_oceania.csv', index_col='country')
print(data)
~~~
{: .language-python}
~~~
             gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  gdpPercap_1967  \ncountry
Australia       10039.59564     10949.64959     12217.22686     14526.12465
New Zealand     10556.57566     12247.39532     13175.67800     14463.91893


             gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  gdpPercap_1987  \ncountry
Australia       16788.62948     18334.19751     19477.00928     21888.88903
New Zealand     16046.03728     16233.71770     17632.41040     19007.19129


             gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  gdpPercap_2007
country
Australia       23424.76683     26997.93657     30687.75473     34435.36744
New Zealand     18363.32494     21050.41377     23189.80135     25185.00911
~~~
{: .output}

## Usare `DataFrame.info` per saperne di più su un dataframe.

~~~
data.info()
~~~
{: .language-python}
~~~
<class 'pandas.core.frame.DataFrame'>
Index: 2 entries, Australia to New Zealand
Data columns (total 12 columns):
gdpPercap_1952    2 non-null float64
gdpPercap_1957    2 non-null float64
gdpPercap_1962    2 non-null float64
gdpPercap_1967    2 non-null float64
gdpPercap_1972    2 non-null float64
gdpPercap_1977    2 non-null float64
gdpPercap_1982    2 non-null float64
gdpPercap_1987    2 non-null float64
gdpPercap_1992    2 non-null float64
gdpPercap_1997    2 non-null float64
gdpPercap_2002    2 non-null float64
gdpPercap_2007    2 non-null float64
dtypes: float64(12)
memory usage: 208.0+ bytes
~~~
{: .output}

*   Questo è un `DataFrame`
*   Due righe, chiamate `'Australia'` e `'New Zealand'`
*   Dodici colonne, ognuna delle quali contiene due valori in virgola mobile a 64 bit.
    *   Più avanti parleremo anche dei valori "nulli", che sono usati per indicare misurazioni mancanti.
*   Usa 208 byte di memoria.

## La variabile `DataFrame.columns` contiene le informazioni relative alle colonne del dataframe.

*   Nota bene, questa è una variabile che contiene dati, *non* un metodo.
    *   Allo stesso modo di `math.pi`.
    *   Per cui, non si usa `()` per chiamarlo.
*   Queste variabili vengono chiamate *membri*.

~~~
print(data.columns)
~~~
{: .language-python}
~~~
Index(['gdpPercap_1952', 'gdpPercap_1957', 'gdpPercap_1962', 'gdpPercap_1967',
       'gdpPercap_1972', 'gdpPercap_1977', 'gdpPercap_1982', 'gdpPercap_1987',
       'gdpPercap_1992', 'gdpPercap_1997', 'gdpPercap_2002', 'gdpPercap_2007'],
      dtype='object')
~~~
{: .output}

## Usare `DataFrame.T` per trasporre un dataframe.

*   A volte, capita di voler trattare le righe come colonne, o viceversa.
*   La trasposta (che si scrive `.T`) non copia i dati in un nuovo dataframe, ma cambia la 'vista' che il programma ha dei dati.
*   Come `columns`, è una variabile membro.

~~~
print(data.T)
~~~
{: .language-python}
~~~
country           Australia  New Zealand
gdpPercap_1952  10039.59564  10556.57566
gdpPercap_1957  10949.64959  12247.39532
gdpPercap_1962  12217.22686  13175.67800
gdpPercap_1967  14526.12465  14463.91893
gdpPercap_1972  16788.62948  16046.03728
gdpPercap_1977  18334.19751  16233.71770
gdpPercap_1982  19477.00928  17632.41040
gdpPercap_1987  21888.88903  19007.19129
gdpPercap_1992  23424.76683  18363.32494
gdpPercap_1997  26997.93657  21050.41377
gdpPercap_2002  30687.75473  23189.80135
gdpPercap_2007  34435.36744  25185.00911
~~~
{: .output}

## Usare `DataFrame.describe` per calcolare le statistiche riassuntive di un insieme di dati.

DataFrame.describe() calcola le statistiche riassuntive delle sole colonne che contengono dati numerici. 
Tutte le altre colonne vengono ignorate, a meno di usare l'argomento `include='all'`.
~~~
print(data.describe())
~~~
{: .language-python}
~~~
       gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  gdpPercap_1967  \ncount        2.000000        2.000000        2.000000        2.000000
mean     10298.085650    11598.522455    12696.452430    14495.021790
std        365.560078      917.644806      677.727301       43.986086
min      10039.595640    10949.649590    12217.226860    14463.918930
25%      10168.840645    11274.086022    12456.839645    14479.470360
50%      10298.085650    11598.522455    12696.452430    14495.021790
75%      10427.330655    11922.958888    12936.065215    14510.573220
max      10556.575660    12247.395320    13175.678000    14526.124650


       gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  gdpPercap_1987  \ncount         2.00000        2.000000        2.000000        2.000000
mean      16417.33338    17283.957605    18554.709840    20448.040160
std         525.09198     1485.263517     1304.328377     2037.668013
min       16046.03728    16233.717700    17632.410400    19007.191290
25%       16231.68533    16758.837652    18093.560120    19727.615725
50%       16417.33338    17283.957605    18554.709840    20448.040160
75%       16602.98143    17809.077557    19015.859560    21168.464595
max       16788.62948    18334.197510    19477.009280    21888.889030


       gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  gdpPercap_2007
count        2.000000        2.000000        2.000000        2.000000
mean     20894.045885    24024.175170    26938.778040    29810.188275
std       3578.979883     4205.533703     5301.853680     6540.991104
min      18363.324940    21050.413770    23189.801350    25185.009110
25%      19628.685413    22537.294470    25064.289695    27497.598692
50%      20894.045885    24024.175170    26938.778040    29810.188275
75%      22159.406358    25511.055870    28813.266385    32122.777857
max      23424.766830    26997.936570    30687.754730    34435.367440
~~~
{: .output}

*   Non è un'operazione particolarmente utile quando abbiamo solo due righe,
    ma può essere molto utile quando ne abbiamo migliaia.

> ## Leggere altri dati
>
> Carica i dati contenuti nel file `gapminder_gdp_americas.csv`
> (che dovrebbe essere nella stessa cartella di `gapminder_gdp_oceania.csv`)
> in una variabile chiamata `americas`
> e mostra le sue statistiche riassuntive.
>
> > ## Soluzione
> > Per leggere da un CSV, usiamo `pd.read_csv` passando il nome del file 'data/gapminder_gdp_americas.csv' alla funzione. Inoltre, passiamo
> > ancora una volta il nome della colonna 'country' al parametro
> >  `index_col` in modo da indicizzare per paese:
> > ~~~
> > americas = pd.read_csv('data/gapminder_gdp_americas.csv', index_col='country')
> > ~~~
> >{: .language-python}
> {: .solution}
{: .challenge}



> ## Esaminare i dati.
>
> Dopo aver letto dal file i dati relativi alle Americhe,
> usa `help(americas.head)` e `help(americas.tail)`
> per scoprire a cosa servono `DataFrame.head` e `DataFrame.tail`.
>
> 1.  Con quale chiamata si possono visualizzare le prime tre righe di questa tabella?
> 2.  Con quale chiamata si possono visualizzare le ultime tre colonne di questa tabella?
>     (Suggerimento: può essere utile invertire la 'vista' sul dataset.)
>
> > ## Soluzione
> > 1. Possiamo dare un'occhiata alle prime cinque righe di `americas` eseguendo `americas.head()` (che ci permette di vedere la 'testa'
> > del DataFrame). Possiamo specificare il numero di righe che desideriamo visualizzare, specificando il parametro `n` nella nostra chiamata
> > a `americas.head()`. Per visualizzare le prime tre righe, esegui:
> >
> > ~~~
> > americas.head(n=3)
> > ~~~
> >{: .language-python}
> > 
> > In questo caso il risultato è
> > ~~~
> >          continent  gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  \n> >country                                                               
> >Argentina  Americas     5911.315053     6856.856212     7133.166023   
> >Bolivia    Americas     2677.326347     2127.686326     2180.972546   
> >Brazil     Americas     2108.944355     2487.365989     3336.585802   
> >
> >           gdpPercap_1967  gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  \n> >country                                                                     
> >Argentina     8052.953021     9443.038526    10079.026740     8997.897412   
> >Bolivia       2586.886053     2980.331339     3548.097832     3156.510452   
> >Brazil        3429.864357     4985.711467     6660.118654     7030.835878   
> >
> >           gdpPercap_1987  gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  \n> >country                                                                     
> >Argentina     9139.671389     9308.418710    10967.281950     8797.640716   
> >Bolivia       2753.691490     2961.699694     3326.143191     3413.262690   
> >Brazil        7807.095818     6950.283021     7957.980824     8131.212843   
> >
> >           gdpPercap_2007  
> >country                    
> >Argentina    12779.379640  
> >Bolivia       3822.137084  
> >Brazil        9065.800825 
> > ~~~ 
> >{: .output}
> > 2. Per dare un'occhiata alle ultime tre righe di `americas`, usiamo il comando `americas.tail(n=3)`,
> > che è analogo a `head()`. Però, in questo caso vogliamo le ultime tre *colonne*, per cui dobbiamo
> > cambiare la 'vista' e usare `tail()`. A questo scopo, creiamo un nuovo 
> > DataFrame in cui righe e colonne sono scambiate.
> > 
> > ~~~
> > americas_invertito = americas.T
> > ~~~
> >{: .language-python}
> >
> > Poi, possiamo visualizzare le ultime tre colonne di `americas` guardando le ultime tre righe di `americas_invertito`:
> > ~~~
> > americas_invertito.tail(n=3)
> > ~~~
> >{: .language-python}
> > E allora il risultato è
> > ~~~
> > country        Argentina  Bolivia   Brazil   Canada    Chile Colombia  \n> > gdpPercap_1997   10967.3  3326.14  7957.98  28954.9  10118.1  6117.36   
> > gdpPercap_2002   8797.64  3413.26  8131.21    33329  10778.8  5755.26   
> > gdpPercap_2007   12779.4  3822.14   9065.8  36319.2  13171.6  7006.58   
> > 
> > country        Costa Rica     Cuba Dominican Republic  Ecuador    ...     \n> > gdpPercap_1997    6677.05  5431.99             3614.1  7429.46    ...      
> > gdpPercap_2002    7723.45  6340.65            4563.81  5773.04    ...      
> > gdpPercap_2007    9645.06   8948.1            6025.37  6873.26    ...      
> > 
> > country          Mexico Nicaragua   Panama Paraguay     Peru Puerto Rico  \n> > gdpPercap_1997   9767.3   2253.02  7113.69   4247.4  5838.35     16999.4   
> > gdpPercap_2002  10742.4   2474.55  7356.03  3783.67  5909.02     18855.6   
> > gdpPercap_2007  11977.6   2749.32  9809.19  4172.84  7408.91     19328.7   
> > 
> > country        Trinidad and Tobago United States  Uruguay Venezuela  
> > gdpPercap_1997             8792.57       35767.4  9230.24   10165.5  
> > gdpPercap_2002             11460.6       39097.1     7727   8605.05  
> > gdpPercap_2007             18008.5       42951.7  10611.5   11415.8  
> > ~~~ 
> >{: .output}
> > Nota: avremmo potuto fare lo stesso in una sola riga di codice, mettendo i comandi in fila:
> > ~~~
> > americas.T.tail(n=3)
> > ~~~
> >{: .language-python}






> {: .solution}
{: .challenge}

> ## Leggere file in altre cartelle
>
> I dati usati nel progetto a cui stai lavorando sono salvati in un file chiamato `microbi.csv`,
> che si trova in una cartella chiamata `dati_sperimentali`.
> Stai facendo le tue analisi in un notebook chiamato `analisi.ipynb`
> in una cartella di fianco, chiamata `tesi`:
>
> ~~~
> cartella_principale
> +-- dati_sperimentali/
> |   +-- microbi.csv
> +-- tesi/
>     +-- analisi.ipynb
> ~~~
> {: .output}
>
> Che valore o valori bisogna passare a `read_csv` per leggere `microbi.csv` dal notebook `analisi.ipynb`?
> 
> > ## Soluzione
> > Nella chiamata a `pd.read_csv`, dobbiamo specificare il percorso per arrivare al file che ci interessa. Prima di tutto, dobbiamo 'uscire' dalla cartella
> > `tesi` usando '../', e poi entrare nella cartella `dati_sperimentali` usando 'dati_sperimentali/'. Solo allora possiamo specificare il nome del file `microbi.csv.
> > Il risultato è il seguente:
> > ~~~
> > data_microbi = pd.read_csv('../dati_sperimentali/microbi.csv')
> > ~~~
> >{: .language-python}
> {: .solution}
{: .challenge}

> ## Salvare dati su disco
> 
> Cosò come esiste una funzione `read_csv` per leggere dati da un file,
> Pandas contiene una funzione `to_csv` per salvare i dataframe su file.
> Usando ciò che hai imparato riguardo alla lettura dei file,
> salva uno dei tuoi dataframe in un file chiamato `dati_lavorati.csv`.
> Per sapere come usare la funzione `to_csv`, puoi usare `help`.
> > ## Soluzione
> > Per salvare il DataFrame `americas` in un file chiamato `dati_lavorati.csv`, esegui il comando seguente:
> > ~~~
> > americas.to_csv('dati_lavorati.csv')
> > ~~~
> >{: .language-python}
> > Per leggere l'aiuto relativo a `to_csv`, puoi, ad esempio, eseguire,
> > ~~~
> > help(americas.to_csv)
> > ~~~
> >{: .language-python}
> > Osserva che `help(to_csv)` dà un errore! Questa è una sottigliezza, dovuta al fatto che `to_csv` NON è una funzione indipendente, ma un metodo,
> > e la chiamata corretta è `americas.to_csv`. 
> {: .solution}
{: .challenge}

