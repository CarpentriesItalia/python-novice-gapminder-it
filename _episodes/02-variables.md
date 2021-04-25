---
title: "Variabili e valori"
teaching: 10
exercises: 10
questions:
- "Come vengono registrati i dati nei programmi?"
objectives:
- "Scrivere programmi che assegnano valori numerici alle variabili, e li usano per fare calcoli."
- "Saper tenere traccia di come cambiano i valori delle variabili in programmi che assegnano valori numerici."
keypoints:
- "Usare le variabili per tenere valori in memoria."
- "Usare `print` per visualizzare i valori."
- "Le variabili restano accessibili da una cella all'altra."
- "Le variabili devono essere definite prima di essere usate."
- "Le variabili si possono usare per fare calcoli."
- "Usare un indice per estrarre un singolo carattere da una stringa."
- "Usare una slice per estrarre una sotto-stringa."
- "Usare la funzione predefinita `len` per sapere la lunghezza di una stringa."
- "Python distingue tra maiuscole e minuscole."
- "Usare nomi sensati per le variabili."
---
## Usare le variabili per tenere valori in memoria

*   Le **variabili** sono nomi associati a valori.
*   In Python, il simbolo `=` assegna il valore sulla destra al nome sulla sinistra.
*   La variabile viene creata non appena le è assegnato un valore.
*   Qui, Python assegna un'età alla variabile `anni`
    e un nome, posto tra virgolette, a una variabile chiamata `nome`.

~~~
anni = 42
nome = 'Ahmed'
~~~
{: .language-python}

*   I nomi delle variabili
    * possono **soltanto** contenere lettere, cifre, e il trattino basso `_` (generalmente usato per separare le parole in nomi lunghi)
    * non possono iniziare con una cifra
    * distinguono tra **minuscole e maiuscole** (anni, Anni e ANNI sono tre variabili differenti)
*   Le variabili con nomi che iniziano con un trattino basso, come `__vera_eta_di_alistair` hanno un significato speciale
    perciò, non li useremo finché non avremo spiegato questa convenzione.

## Usare `print` per visualizzare valori

*   Python ha una funzione predefinita chiamata `print` (stampa) che visualizza i valori in forma di testo.
*   Chiama la funzione (cioè, di' a Python di eseguirla) usandone il nome.
*   Passa valori alla funzione (cioè gli oggetti da stampare) mettendoli tra parentesi.
*   Per aggiungere una stringa ai valori stampati, mettila tra virgolette singole o doppie.
*   I valori passati alla funzione si chiamano **argomenti**

~~~
print(nome, 'ha', anni, 'anni')
~~~
{: .language-python}
~~~
Ahmed ha 42 anni
~~~
{: .output}

*   `print` inserisce automaticamente un singolo spazio tra i diversi oggetti, per separarli.
*   E va automaticamente a capo alla fine.

## Le variabili devono essere definite prima di essere usate.

*   Se una variabile non esiste ancora, o se il nome è stato scritto sbagliato,
    Python restituisce un errore. (A differenza di altri linguaggi, che cercano di "indovinare" un valore predefinito.)

~~~
print(cognome)
~~~
{: .language-python}
~~~
---------------------------------------------------------------------------
NameError                                 Traceback (most recent call last)
<ipython-input-1-c1fbb4e96102> in <module>()
----> 1 print(cognome)

NameError: name 'cognome' is not defined
~~~
{: .error}

*   L'ultima riga dei messaggi di errore è di solito quella più utile.
*   Ci occuperemo dei messaggi d'errore più in dettaglio [più avanti]({{ page.root }}/15-scope/#reading-error-messages).

> ## Le variabili restano accessibili da una cella all'altra
>
> Notate che ciò che è importante usando il Jupyter notebook è l'*ordine di esecuzione* delle celle, non l'ordine 
> in cui compaiono. Python tiene a mente *tutto* il codice che è stato eseguito in precedenza, incluse le variabili che sono state definite,
> indipendentemente dall'ordine in cui sono scritte nel notebook. Per cui, se definisci una variabile più in basso
> e poi esegui o riesegui celle più in alto, quelle definite in basso esisteranno ancora. Per esempio, crea due celle con il seguente contenuto, nell'ordine:
>
> ~~~
> print(mio_valore)
> ~~~
> {: .language-python}
>
> ~~~
> mio_valore = 1
> ~~~
> {: .language-python}
>
> Se esegui le due celle in ordine, la prima darà un errore. Però, se esegui la prima cella *dopo* la seconda,
> stamperà `1`. Per evitare confusione, può essere utile usare l'opzione `Kernel` -> `Restart & Run All` (riavvia e esegui tutto), che
> ripulisce l'interprete e esegue tutte le celle dall'alto in basso ripartendo da zero.
{: .callout}

## Le variabili si possono usare per fare calcoli.

*   Possiamo usare variabili nei calcoli come se fossero numeri.
    *   Ricorda che, poche righe più in su, abbiamo assegnato il valore `42` alla variabile `anni`.

~~~
anni = anni + 3
print('Età tra tre anni:', anni)
~~~
{: .language-python}
~~~
Età tra tre anni: 45
~~~
{: .output}

## Usare un indice per estrarre un singolo carattere da una stringa.

*   I caratteri (le singole lettere, numeri, eccetera) che formano una stringa
    sono ordinati. Per esempio, la stringa `'AB'` non è la stessa cosa di `'BA'`. A causa di questo
    ordinamento, possiamo trattare la stringa come una lista di caratteri.
*   Ogni posizione nella stringa (prima, seconda, ecc.) corrisponde a un numero. Questo
    numero è detto **indice**.
*   Gli indici sono contati a partire da 0.
*   Per ottenere il carattere corrispondente a una certa posizione, si usa il relativo indice tra parentesi quadre.

![un esempio di indicizzazione](../fig/2_indexing.svg)

~~~
nome_atomo = 'elio'
print(nome_atomo[0])
~~~
{: .language-python}
~~~
e
~~~
{: .output}

## Usare una slice per estrarre una sotto-stringa.

*   Una parte di una stringa si chiama **sotto-stringa** (substring). Una sotto-stringa può essere formata anche solo da
    un carattere singolo.
*   Un membro di una lista è detto elemento della lista. Quando trattiamo una stringa
    come fosse una lista, gli elementi della stringa sono i suoi singoli caratteri.
*   Una *slice* (fetta) è una parte di una stringa (o, più in generale, di qualsiasi cosa analoga a una lista).
*   Si estrae una slice (o si "affetta" una lista) scrivendo `[inizio:fine]`, dove `inizio` è sostituito dall'
    indice del primo elemento che vogliamo, e `fine` è sostituito dall'indice dell'elemento immediatamente
    successivo all'ultimo elemento che vogliamo.
*   Matematicamente, possiamo dire che la slice seleziona l'intervallo `[inizio, fine)`.
*   La differenza tra `fine` e `inizio` è la lunghezza della slice.
*   Estrarre una slice non cambia i contenuti della stringa originale. Al contrario,
    la slice è una copia di parte della stringa originale.

~~~
nome_atomo = 'sodio'
print(nome_atomo[0:3])
~~~
{: .language-python}
~~~
sod
~~~
{: .output}

## Usare la funzione predefinita `len` per sapere la lunghezza di una stringa.

~~~
print(len('elio'))
~~~
{: .language-python}
~~~
4
~~~
{: .output}

*   Le funzioni eseguite una dentro l'altra sono chiamate dall'interno all'esterno.
     come in matematica.

## Python distingue tra maiuscole e minuscole

*   Python nota la differenza tra lettere maiuscole e minuscole,
    perciò `Nome` and `nome` sono due variabili diverse.
*   Poiché ci sono convenzioni sull'uso delle lettere maiuscole all'inizio dei nomi di variabili, per ora useremo le lettere minuscole.

## Usare nomi sensati per le variabili.

*   Dal punto di vista di Python, non è importante il nome dato alle variabili, purché seguano le regole dette
    (caratteri alfanumerici e trattino basso).

~~~
flabadab = 42
ewr_422_yY = 'Ahmed'
print(ewr_422_yY, 'ha', flabadab, 'anni')
~~~
{: .language-python}

*   Usa nomi di variabili dal significato chiaro, in modo da aiutare gli altri a capire cosa faccia il tuo programma.
*   Tra questi "altri", il più importante è te stesso nel futuro.

> ## Scambiare valori
>
> Completa la tabella indicando i valori delle variabili in questo programma
> *dopo* l'esecuzione di ogni istruzione.
>
> ~~~
> # Comando  # Valore di x   # Valore di y   # Valore di scambio #
> x = 1.0     #              #              #               #
> y = 3.0     #              #              #               #
> scambio = x #              #              #               #
> x = y       #              #              #               #
> y = scambio #              #              #               #
> ~~~
> {: .language-python}
> > ## Soluzione
> >
> > ~~~
> > # Comando # Valore di x # Valore di y # Valore di scambio #
> > x = 1.0     # 1.0          # non definito # non definito  #
> > y = 3.0     # 1.0          # 3.0          # non definito  #
> > scambio = x # 1.0          # 3.0          # 1.0           #
> > x = y       # 3.0          # 3.0          # 1.0           #
> > y = scambio # 3.0          # 1.0          # 1.0           #
> > ~~~
> > {: .output}
> > 
> > Queste tre righe scambiano i valori di `x` e `y` usando la variabile `scambio`
> > come memoria temporanea. È un metodo abbastanza comune in programmazione.
>{: .solution}
{: .challenge}

> ## Prevedere i valori
>
> Qual è il valore finale di `posizione` nel programma seguente?
> (Prova a prevedere il valore senza eseguire il programma,
> poi verifica la tua previsione.)
>
> ~~~
> inizio = 'sinistra'
> posizione = inizio
> inizio = 'destra'
> ~~~
> {: .language-python}
> > ## Solution
> >
> > ~~~
> > 'sinistra'
> > ~~~
> > {: .output}
> >
>> Alla variabile `inizio` è assegnato il valore `'sinistra'`.
> > Nella seconda riga, la variabile `posizione` riceve anch'essa il valore
>> `'sinistra'`. Nella terza riga, alla variabile `inizio` è assegnato il
>> valore `'destra'`, ma la variabile `posizione` mantiene il valore
>> di `'sinistra'`.
>{: .solution}
{: .challenge}

> ## Sfida
>
> Se definisci `a = 123`,
> cosa succede se provi a ottenere la seconda cifra di `a` usando `a[1]`?
>
> > ## Soluzione
> > I numeri non sono né stringhe né sequenze e Python darà un errore se cerchi di fare un'operazione con gli indici
> > su un numero. Nella prossima lezione su [tipi e conversioni di tipo]({{ page.root }}/03-types-conversion/#convert-numbers-and-strings)
> > impareremo altri concetti sui tipi e su come convertire da un tipo ad un altro. Se ti serve l'N-esima cifra di un numero,
> > puoi convertirlo in una stringa usando la funzione predefinita `str` e poi fare l'operazione con gli indici sulla stringa risultante.
> >
> > ~~~
> > a = 123
> > print(a[1])
> > ~~~
> > {: .language-python}
> > ~~~
> > TypeError: 'int' object is not subscriptable
> > ~~~
> > {: .error}
> > 
> > 
> > ~~~
> > a = str(123)
> > print(a[1])
> > ~~~
> > {: .language-python}
> > ~~~
> > 2
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Scegliere un nome
>
> Quale di questi è un nome migliore per una variabile, `m`, `min`, o `minuti`?
> Perché?
> Suggerimento: pensa a quale codice tra i seguenti preferiresti ricevere in eredità
> da qualcuno che sta lasciando a te il suo lavoro:
>
> 1. `ts = m * 60 + s`
> 2. `tot_sec = min * 60 + sec`
> 3. `total_seconds = minutes * 60 + seconds`
>
> > ## Soluzione
> >
> > `minuti` è meglio, perché `min` potrebbe indicare qualcosa come "minimo"
> > (e infatti è una funzione predefinita esistente in Python, che tratteremo più avanti).
> {: .solution}
{: .challenge}

> ## Pratica con le slice
>
> Che cosa stampa il seguente programma?
>
> ~~~
> nome_atomo = 'carbonio'
> print('nome_atomo[1:3] è:', nome_atomo[1:3])
> ~~~
> {: .language-python}
>
> > ## Soluzione
> >
> > ~~~
> > nome_atomo[1:3] è: ar
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Concetti sulle slice
>
> 1.  Cosa fa `qualcosa[inizio:fine]`?
> 2.  Cosa fa `qualcosa[inizio:]` (senza un valore dopo i due punti)?
> 3.  Cosa fa `qualcosa[:fine]` (senza un valore prima dei due punti)?
> 4.  Cosa fa `qualcosa[:]` (solo i due punti)?
> 5.  Cosa fa `qualcosa[numero:un-numero-negativo]`?
> 6.  Cosa succede quando scegli un valore di `fine` che è fuori dai limiti? (per esempio, prova `nome_atomo[0:15]`) 
>
> > ## Soluzioni
> >
> > 1. `qualcosa[inizio:fine]` restituisce una "fetta" da `inizio` fino al valore precedente a `fine`
> > 2. `qualcosa[inizio:]` restituisce una fetta da `low` fino alla fine di `qualcosa`
> > 3. `qualcosa[:fine]` restituisce una fetta dal principio di `qualcosa` fino al valore precedente a `fine`
> > 4. `qualcosa[:]` restituisce interamente `qualcosa`
> > 5. `qualcosa[numero:un-numero-negativo]` restituisce una fetta da `numero` fino a `un-numero-negativo` valori contati dalla fine di `qualcosa`.
> > 6. Se una parte della slice è fuori dai limiti, l'operazione non fallisce. `nome_atomo[0:15]` dà lo stesso risultato di `nome_atomo[0:]`.
> {: .solution}
{: .challenge}

