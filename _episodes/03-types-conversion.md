---
title: "Tipi di dati e conversioni di tipo"
teaching: 10
exercises: 10
questions:
- "Quali tipi di dati si possono memorizzare in un programma?"
- "Come si possono convertire dati da un tipo a un altro?"
objectives:
- "Spiegare le principali differenze tra gli interi e i numeri a virgola mobile."
- "Spiegare le principali differenze tra numeri e stringhe di caratteri."
- "Usare funzioni predefinite per convertire tra interi, numeri a virgola mobile e stringhe."
keypoints:
- "Ogni valore ha un tipo."
- "Per scoprire il tipo di una variabile, si usa la funzione predefinita `type`."
- "In base al tipo, le operazioni che si possono fare su un valore sono diverse."
- "Le stringhe possono essere sommate e moltiplicate."
- "Le stringhe hanno una lunghezza, i numeri no."
- "Lavorando su stringhe e numeri, è necessario convertire stringhe in numeri o viceversa."
- "Gli interi e i numeri a virgola mobile possono essere usati insieme liberamente in operazioni matematiche."
- "Le variabili possono cambiare valore solo quando un nuovo valore viene loro assegnato."
---
## Tutti i valori hanno un tipo.

*   In un programma, ogni valore è di uno specifico tipo.
*   Intero (integer, `int`): rappresenta numeri interi positivi o negativi, come 3 or -512.
*   Numero a virgola mobile (`float`): rappresenta numeri reali come 3.14159 o -2.5. Notare che il separatore decimale è il punto, `.`, come nell'uso anglofono, e non la virgola, `,`, come si usa generalmente in italiano.
*   Stringa di caratteri (normalmente chiamata "string" o "stringa", `str`): del testo.
    *   Può essere scritta o in virgolette alte singole o in virgolette alte doppie (purché l'uso sia coerente).
    *   Le virgolette non vengono stampate quando la stringa viene visualizzata.

## Per scoprire il tipo di una variabile, si usa la funzione predefinita `type`.

*   Per scoprire qual è il tipo corrispondente a un valore, usa la funzione predefinita `type`.
*   Funziona anche sulle variabili.
    *   Ma non dimenticare che è il *valore* ad avere quel tipo; la *variabile* è solo un'etichetta.

~~~
print(type(52))
~~~
{: .language-python}
~~~
<class 'int'>
~~~
{: .output}

~~~
fitness = 'average'
print(type(fitness))
~~~
{: .language-python}
~~~
<class 'str'>
~~~
{: .output}

## In base al tipo, le operazioni che si possono fare su un valore sono diverse.

*   È il tipo di un valore a determinare che cosa il programma può fare con quel valore.

~~~
print(5 - 3)
~~~
{: .language-python}
~~~
2
~~~
{: .output}

~~~
print('ciao' - 'c')
~~~
{: .language-python}
~~~
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-2-67f5626a1e07> in <module>()
----> 1 print('ciao' - 'c')

TypeError: unsupported operand type(s) for -: 'str' and 'str'
~~~
{: .error}

## Si possono usare gli operatori "+" e "*" anche sulle stringhe.

*   Il simbolo di addizione concatena le stringhe l'una all'altra.

~~~
nome = 'Ahmed' + ' ' + 'Walsh'
print(nome)
~~~
{: .language-python}
~~~
Ahmed Walsh
~~~
{: .output}

*   Moltiplicare una stringa di caratteri per un numero intero _N_ crea una nuova stringa che consiste di quella stringa di caratteri ripetuta _N_ volte.
    *   Poiché la moltiplicazione è un'addizione ripetuta.

~~~
separatore = '=' * 10
print(separatore)
~~~
{: .language-python}
~~~
==========
~~~
{: .output}

## Le stringhe hanno una lunghezza, i numeri no.

*   La funzione predefinita `len` conta il numero di caratteri in una stringa

~~~
print(len(nome))
~~~
{: .language-python}
~~~
11
~~~
{: .output}

*   Ma i numeri non hanno una lunghezza (nemmeno zero).

~~~
print(len(52))
~~~
{: .language-python}
~~~
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-3-f769e8e8097d> in <module>()
----> 1 print(len(52))

TypeError: object of type 'int' has no len()
~~~
{: .error}

## <a name='convert-numbers-and-strings'></a> Lavorando su stringhe e numeri, è necessario convertire stringhe in numeri o viceversa.

*   Non è possibile sommare numeri e stringhe insieme.

~~~
print(1 + '2')
~~~
{: .language-python}
~~~
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-4-fe4f54a023c6> in <module>()
----> 1 print(1 + '2')

TypeError: unsupported operand type(s) for +: 'int' and 'str'
~~~
{: .error}

*   Non è permesso in quanto ambiguo: `1 + '2'` dovrebbe risultare in `3` o in `'12'`?
*   Alcuni tipi possono essere convertiti in altri usando il nome del tipo come una funzione.

~~~
print(1 + int('2'))
print(str(1) + '2')
~~~
{: .language-python}
~~~
3
12
~~~
{: .output}

## Gli interi e i numeri a virgola mobile possono essere usati insieme liberamente in operazioni matematiche.

*   Gli interi e i float (numeri a virgola mobile) possono essere mescolati nelle operazioni aritmetiche.
    *   Python 3 converte automaticamente gli interi in float quando è necessario. (La divisione tra interi in Python 2 ritornava un intero, il quoziente intero approssimato per difetto.)

~~~
print('un mezzo è', 1 / 2.0)
print('tre al quadrato è', 3.0 ** 2)
~~~
{: .language-python}
~~~
un mezzo è 0.5
tre al quadrato è 9.0
~~~
{: .output}

## Le variabili possono cambiare valore solo quando un nuovo valore viene loro assegnato

*   In un foglio di calcolo, se facciamo dipendere una cella da un'altra,
    e modifichiamo il contenuto di quest'ultima,
    la prima si aggiorna automaticamente.
*   Questo **non** succede nei linguaggi di programmazione.

~~~
prima = 1
seconda = 5 * prima
prima = 2
print('la prima è', prima, 'e la seconda è', seconda)
~~~
{: .language-python}
~~~
la prima è 2 e la seconda è 5
~~~
{: .output}

*   Nel fare la moltiplicazione, il computer legge il valore di `prima`,
    crea un nuovo valore, e lo assegna a `seconda`.
*   Dopodiché, `seconda` non si ricorda la propria origine.

> ## Frazioni
>
> Di che tipo è il valore 3.4?
> Come si può scoprire?
>
> > ## Soluzione
> >
> > È un numero a virgola mobile (floating point number, spesso abbreviato "float").
> >
> > ~~~
> > print(type(3.4))
> > ~~~
> > {: .language-python}
> > ~~~
> > <class 'float'>
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Conversione di tipo automatica
>
> Di che tipo è il valore 3.25 + 4?
>
> > ## Soluzione
> >
> > È un float:
> > gli interi sono automaticamente convertiti in float quando necessario.
> >
> > ~~~
> > risultato = 3.25 + 4
> > print(risultato, 'è un', type(risultato))
> > ~~~
> > {: .language-python}
> > ~~~
> > 7.25 è un <class 'float'>
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Scegliere un tipo
>
> Che tipo di valore (intero, numero a virgola mobile, o stringa di caratteri)
> useresti per rappresentare gli esempi che seguono? Prova a cercare più di una risposta valida
> per ogni problema. Per esempio, nel n. 1, in quali casi avrebbe più senso contare i giorni con una
> variabile a virgola mobile rispetto a un intero?
>
> 1. Il numero dei giorni passati dall'inizio dell'anno.
> 2. Il tempo passato dall'inizio dell'anno ad oggi, espresso in giorni.
> 3. Il numero di serie di uno strumento di laboratorio.
> 4. L'età di un campione da laboratorio.
> 5. L'attuale popolazione di una città.
> 6. La popolazione media di una città nel tempo.
>
> > ## Soluzione
> >
> > Le risposte sono:
> > 1. Intero, dal momento che il numero di giorni sarà compreso tra 1 e 365. 
> > 2. A virgola mobile, dal momento che serviranno frazioni di giorni.
> > 3. Una stringa di caratteri se il numero di serie contiene numeri e lettere, altrimenti un intero se il numero di serie consiste di sole cifre.
> > 4. Dipende! Come è definita l'età del campione? in giorni completi a partire dalla raccolta (intero)? una data e un'ora (stringa)?
> > 5. Scegli un numero a virgola mobile per rappresentare la popolazione in grandi quantità (p. es. milioni), o un intero per rappresentare la popolazione in unità di individui.
> > 6. Un float, dal momento che una media probabilmente avrà valori frazionari.
> > {: .output}
> {: .solution}
{: .challenge}

> ## Tipi di divisioni
>
> In Python 3, l'operatore `//` esegue la divisione intera (con quoziente intero senza resto, 
> approssimando per difetto), l'operatore `/` effettua la divisione con la virgola,
> e l'operatore '%' (detto *modulo*) calcola e restituisce il resto della divisione intera:
>
> ~~~
> print('5 // 3:', 5//3)
> print('5 / 3:', 5/3)
> print('5 % 3:', 5%3)
> ~~~
> {: .language-python}
>
> ~~~
> 5 // 3: 1
> 5 / 3: 1.6666666666666667
> 5 % 3: 2
> ~~~
> {: .output}
>
> Tuttavia, in Python2 (e altri linguaggi), l'operatore `/` tra due tipi interi esegue la divisione intera (`//`) division. Per fare una divisione con la virgola, siamo costretti a convertire uno degli interi in float.
>
> ~~~
> print('5 // 3:', 1)
> print('5 / 3:', 1 )
> print('5 / float(3):', 1.6666667 )
> print('float(5) / 3:', 1.6666667 )
> print('float(5 / 3):', 1.0 )
> print('5 % 3:', 2)
> ~~~
>
> Se `n_soggetti` è il numero di soggetti che partecipano a uno studio,
> e `n_per_sondaggio` è il numero che partecipa a un singolo sondaggio,
> scrivi un'espressione che calcola il numero di sondaggi necessari
> a raggiungere tutti i partecipanti una volta.
>
> > ## Soluzione
> > Vogliamo sapere il numero di sondaggi che raggiungono tutti una volta, che è
> > il valore approssimato per eccesso di `n_soggetti / n_per_sondaggio`. Ciò è lo stesso che 
> > eseguire una divisione intera con `//` e aggiungere 1.
> > ~~~
> > n_soggetti = 600
> > n_per_sondaggio = 42
> > n_sondaggi = n_soggetti // n_per_sondaggio + 1
> >
> > print(n_soggetti, 'soggetti,', n_per_sondaggio, 'per sondaggio:', n_sondaggi)
> > ~~~
> > {: .language-python}
> > ~~~
> > 600 soggetti, 42 per sondaggio: 15
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Da stringhe a numer
>
> Ogniqualvolta sia ragionevolmente possibile, `float()` è in grado di convertire una stringa in un float,
> e `int()` converte un float in un intero:
>
> ~~~
> print("da stringa a float:", float("3.4"))
> print("da float a int:", int(3.4))
> ~~~
> {: .language-python}
>
> ~~~
> da stringa a float: 3.4
> da float a int: 3
> ~~~
> {: .output}
>
> Se la conversione non ha senso, però, appare un messaggio di errore>
> ~~~
> print("da stringa a float:", float("Hello world!"))
> ~~~
> {: .language-python}
>
> ~~~
> ---------------------------------------------------------------------------
> ValueError                                Traceback (most recent call last)
> <ipython-input-5-df3b790bf0a2> in <module>()
> ----> 1 print("da string a float:", float("Hello world!"))
>
> ValueError: could not convert string to float: 'Hello world!'
> ~~~
> {: .error}
>
> Date queste informazioni, cosa ti aspetti che faccia questo programma?
>
> Che cosa fa in realtà?
>
> Perche, secondo te, fa così?
>
> ~~~
> print("stringa frazionaria a intero:", int("3.4"))
> ~~~
> {: .language-python}
> 
> > ## Solution
> > Non sarebbe irragionevole aspettarsi che il comando `int` in Python 3 converta la stringa
> > "3.4" in 3.4 e poi faccia un'ulteriore conversione di tipo arrivando a 3. Dopo tutto Python 3
> > fa un sacco di altre magie: il bello è quello.
> > 
> > Eppure, Python 3 ci dà un errore. Perché? Forse, per essere coerente. Se si chiede a Python di fare
> > due "typecasts" (conversioni di tipo), bisogna farle esplicitamente nel codice.
> >
> > ~~~
> > int("3.4")
> > int(float("3.4"))
> > ~~~
> > {: .language-python}
> > ~~~
> > In [2]: int("3.4")
> > ---------------------------------------------------------------------------
> > ValueError                                Traceback (most recent call last)
> > <ipython-input-2-ec6729dfccdc> in <module>()
> > ----> 1 int("3.4")
> > ValueError: invalid literal for int() with base 10: '3.4'
> > 3
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Aritmetica con tipi diversi
>
> Quali delle opzioni seguenti ci restituiranno il numero `2.0` in virgola mobile?
> Nota: può esserci più di una risposta esatta.
>
> ~~~
> prima = 1.0
> seconda = "1"
> terza = "1.1"
> ~~~
> {: .language-python}
>
> 1. `prima + float(seconda)`
> 2. `float(seconda) + float(terza)`
> 3. `first + int(terza)`
> 4. `first + int(float(terza))`
> 5. `int(prima) + int(float(terza))`
> 6. `2.0 * seconda`
>
> > ## Soluzione
> >
> > Risposta: 1 e 4
> {: .solution}
{: .challenge}

> ## Numeri complessi
>
> Python offre l'uso dei numeri complessi,
> che si scrivono `1.0+2.0j`.
> Se `val` è un numero immaginario,
> si può accedere alle sua parti reale e immaginaria usando la *notazione punto*
> cioè `val.real` e `val.imag`.
>
> ~~~
> complesso = 6 + 2j
> print(complesso.real)
> print(complesso.imag)
> ~~~
> {: .language-python}
>
> ~~~
> 6.0
> 2.0
> ~~~
> {: .output}
>
>
> 1.  Perché, secondo te, Python usa `j` instead of `i` per la parte immaginaria?
> 2.  Cosa ti aspetti che sia il risultato di `1+2j + 3`?
> 3.  Cosa ti aspetti che sia `4j`?  E invece `4 j` oppure `4 + j`?
> 
> > ## Soluzione
> >
> > 1. L'uso matematico standard è tipicamente quello di indicare un numero immaginario con `i`. Tuttavia, da quanto dicono i media,
> > l'uso di `j` è una vecchia convenzione usata in ingegneria elettrica che sarebbe ora difficile cambiare. [Stack Overflow contiene spiegazioni e discussioni
> > ulteriori.](http://stackoverflow.com/questions/24812444/why-are-complex-numbers-in-python-denoted-with-j-instead-of-i)
> > 2. `(4+2j)`
> > 3. `4j`, `Syntax Error: invalid syntax`, in questo caso _j_ è considerata una variabile, e il risultato dipende da se _j_ è definita e, se lo è, dal suo valore assegnato.
> {: .solution}
{: .challenge}

