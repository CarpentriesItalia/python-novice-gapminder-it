---
title: "Funzioni predefinite e aiuto"
teaching: 15
exercises: 10
questions:
- "Come si usano le funzioni predefinite?"
- "Come si fa a sapere cosa fanno?"
- "Quali sono i tipi di errori che possono presentarsi in un programma?"
objectives:
- "Spiegare a cosa servono le funzioni."
- "Chiamare correttamente le funzioni predefinite di Python."
- "Usare correttamente funzioni predefinite nidificate una dentro l'altra."
- "Usare l'aiuto per visualizzare la documentazione di funzioni predefinite."
- "Descrivere correttamente i casi in cui possono presentarsi SyntaxError e NameError."
keypoints:
- "Usare i commenti per aggiungere documentazione ai programmi."
- "Una funzione può ricevere zero o più argomenti."
- "Tra le funzioni predefinite più comuni ci sono `max`, `min` e `round`."
- "Le funzioni possono funzionare solo con certe combinazioni di argomenti."
- "Le funzioni possono avere valori predefiniti per alcuni argomenti."
- "Usare la funzione predefinita `help` per ottenere aiuto relativamente a una funzione."
- "Il Jupyter Notebook ha due modi di mostrare l'aiuto."
- "Tutte le funzioni restituiscono qualcosa."
- "Python mostra un errore di sintassi quando non riesce a capire il codice sorgente di un programma."
- "Python mostra un errore runtime quanto qualcosa non funziona mentre il programma viene eseguito."
- "Gli errori di sintassi si risolvono rileggendo il codice sorgente, gli errori runtime tracciando l'esecuzione del programma."
---
## Usare i commenti per aggiungere documentazione ai programmi.

~~~
# Questa frase non verrà eseguita da Python.
adjustment = 0.5   # Nemmeno questa: tutto ciò che si trova dopo un '#' viene ignorato.
~~~
{: .language-python}

## Una funzione può ricevere zero o più argomenti.

*   Abbiamo già visto alcuni esempi di funzioni. Ora, diamo un'occhiata più da vicino.
*   Una *argomento* è un valore passato a una funzione.
*   `len` ne richiede esattamente uno.
*   `int`, `str`, e `float` creano un nuovo valore a partire da uno esistente.
*   `print` ne richiede zero o più.
*   `print` senza argomenti stampa una riga di testo vuota.
    *   Le parentesi vanno sempre usate, anche quando sono vuote,
        così che Python sappia che stiamo chiamando una funzione.

~~~
print('prima')
print()
print('dopo')
~~~
{: .language-python}
~~~
prima

dopo
~~~
{: .output}

## Tra le funzioni predefinite più comuni ci sono `max`, `min` e `round`.

*   Si usa `max` per trovare il massimo tra uno o più valori.
*   Si usa `min` per trovare il minimo.
*   Entrambi funzionano sia sui numeri che sulle stringhe di caratteri.
    *   Il concetto di "maggiore" e "minore" usa l'ordinamento (0-9, A-Z, a-z) per i caratteri.

~~~
print(max(1, 2, 3))
print(min('a', 'A', '0'))
~~~
{: .language-python}
~~~
3
0
~~~
{: .output}

## Le funzioni possono funzionare solo con certe combinazioni di argomenti.

*   `max` e `min` richiedono almeno un argomento.
    *   "Qual è valore massimo di un insieme vuoto" è una domanda priva di senso.
*   Inoltre, devono ricevere input che possono essere confrontati tra loro in modo sensato.

~~~
print(max(1, 'a'))
~~~
{: .language-python}
~~~
TypeError                                 Traceback (most recent call last)
<ipython-input-52-3f049acf3762> in <module>
----> 1 print(max(1, 'a'))

TypeError: '>' not supported between instances of 'str' and 'int'
~~~
{: .error}

## Le funzioni possono avere valori predefiniti per alcuni argomenti.

*   `round` arrotonda i numeri a virgola mobile.
*   Di default, arrotonda a zero cifre decimali.

~~~
round(3.712)
~~~
{: .language-python}
~~~
4
~~~
{: .output}

*   Si può specificare il numero di cifre decimali desiderato.

~~~
round(3.712, 1)
~~~
{: .language-python}
~~~
3.7
~~~
{: .output}

## Usare la funzione predefinita `help` per ottenere aiuto relativamente a una funzione.

*   Tutte le funzioni predefinite hanno una documentazione in linea.

~~~
help(round)
~~~
{: .language-python}
~~~
Help on built-in function round in module builtins:

round(number, ndigits=None)
    Round a number to a given precision in decimal digits.

    The return value is an integer if ndigits is omitted or None.  Otherwise
    the return value has the same type as the number.  ndigits may be negative.
~~~
{: .output}

## Python mostra un errore di sintassi quando non riesce a capire il codice sorgente di un programma.

*   Non prova nemmeno a eseguire il programma, se la sua sintassi non può essere analizzata.

~~~
# Qui abbiamo dimenticato di chiudere le virgolette attorno alla stringa.
nome = 'Feng
~~~
{: .language-python}
~~~
  File "<ipython-input-56-f42768451d55>", line 2
    nome = 'Feng
                ^
SyntaxError: EOL while scanning string literal
~~~
{: .error}

~~~
# Un '=' di troppo nella definizione.
anni = = 52
~~~
{: .language-python}
~~~
  File "<ipython-input-57-ccc3df3cf902>", line 2
    anni = = 52
          ^
SyntaxError: invalid syntax
~~~
{: .error}

*   Osserva il messaggio di errore con attenzione:

~~~
print("hello world"
~~~
{: .language-python}
~~~
  File "<ipython-input-6-d1cc229bf815>", line 1
    print ("hello world"
                        ^
SyntaxError: unexpected EOF while parsing
~~~
{: .error}

*   Il messaggio segnala un problema alla prima riga dell'input ("line 1").
    *   In questo caso, il nome del file "ipython-input" indica che
        stiamo lavorando con un input dato a IPython,
        l'interprete Python usato dal Jupyter Notebook.
*   La parte `-6-` del nome del file indica che
    l'errore si è verificato nella cella 6 del nostro Notebook.
*   Dopo, è indicata la riga di codice problematica,
    con il problema indicato da un puntatore `^`.

## <a name='runtime-error'></a> Python mostra un errore runtime quando qualcosa non funziona mentre il programma viene eseguito.

~~~
anni = 53
rimanenti = 100 - annni # 'anni' è scritto sbagliato
~~~
{: .language-python}
~~~
NameError                                 Traceback (most recent call last)
<ipython-input-59-1214fb6c55fc> in <module>
      1 anni = 53
----> 2 rimanenti = 100 - annni # 'anni' è scritto sbagliato

NameError: name 'annni' is not defined
~~~
{: .error}

*   Gli errori di sintassi si risolvono rileggendo il codice sorgente, gli errori runtime tracciando l'esecuzione del programma.

## Il Jupyter Notebook ha due modi per ottenere aiuto.

*   Muovi il cursore ovunque in una chiamata a una funzione
    (cioè, nel nome della funzione o tra i suoi parametri),
    tieni premuto `shift`,
    e premi `tab`.
*   Oppure scrivi il nome di una funzione seguito da un punto di domanda.

## Tutte le funzioni restituiscono qualcosa.

*   Ogni chiamata a funzione produce un risultato.
*   Se la funzione non ha un risultato utile da restituire,
    normalmente restituisce il valore speciale `None` ("Nulla").

~~~
risultato = print('esempio')
print('il risultato di print è', risultato)
~~~
{: .language-python}
~~~
esempio
il risultato di print è None
~~~
{: .output}

> ## L'ordine di esecuzione
>
> 1. Spiega in modo semplice l'ordine delle operazioni nel seguente programma:
>    quando si verifica l'addizione, quando la sottrazione,
>    quando avviene la chiamata ad ognuna delle funzioni, ecc.
> 2. Qual è il valore finale di `radianza`?
>
> ~~~
> radianza = 1.0
> radianza = max(2.1, 2.0 + min(radianza, 1.1 * radianza - 0.5))
> ~~~
> {: .language-python}
> > ## Soluzione
> > 1.
> >    1. `1.1 * radianza = 1.1`
> >    2. `1.1 - 0.5 = 0.6`
> >    3. `min(radianza, 0.6) = 0.6`
> >    4. `2.0 + 0.6 = 2.6`
> >    5. `max(2.1, 2.6) = 2.6`
> > 2. Alla fine, `radianza = 2.6`
> {: .solution}
{: .challenge}

> ## Trova le differenze
>
> 1. Cerca di prevedere che cosa sarà stampato da ognuna delle chiamate a `print` seguenti.
> 2. `max(len(rich), poor)` funziona o produce un messaggio di errore?
>    Se funziona, pensi che il risultato abbia senso?
>
> ~~~
> stringa_facile = "abc"
> print(max(stringa_facile))
> ricco = "argento"
> povero = "stagno"
> print(max(ricco, povero))
> print(max(len(ricco), len(povero)))
> ~~~
> {: .language-python}
> > ## Soluzione
> > ~~~
> > print(max(stringa_facile))
> > ~~~
> > {: .language-python}
> > ~~~
> > c
> > ~~~
> > {: .output}
> > ~~~
> > print(max(ricco, povero))
> > ~~~
> > {: .language-python}
> > ~~~
> > stagno
> > ~~~
> > {: .output}
> > ~~~
> > print(max(len(ricco), len(povero)))
> > ~~~
> > {: .language-python}
> > ~~~
> > 7
> > ~~~
> > {: .output}
> > `max(len(ricco), povero)` restituisce un TypeError (errore di tipo). L'operazione si traduce in `max(7, 'stagno')` e 
> > come abbiamo detto in precedenza, non c'è un modo sensato di confrontare una stringa e un intero.
> > ~~~
> > TypeError                                 Traceback (most recent call last)
> > <ipython-input-65-bc82ad05177a> in <module>
> > ----> 1 max(len(ricco), povero)
> > 
> > TypeError: '>' not supported between instances of 'str' and 'int'
> > ~~~
> > {: .error }
> {: .solution}
{: .challenge}

> ## Perché no?
>
> Perché `max` e `min` non ritornano `None` quando non ricevono argomenti?
>
> > ## Soluzione
> > `max` e `min` restituiscono dei TypeError in questo caso, perché non gli abbiamo dato il numero
> > giusto di parametri. Se restituisse `None`, l'errore sarebbe molto più difficile da trovare, perché
> > verrebbe probabilmente registrato in una variabile e usato più avanti nel programma,
> > probabilmente causando un runtime error.
> {: .solution}
{: .challenge}

> ## L'ultimo carattere in una stringa
>
> Se Python inizia a contare da zero,
> e `len` restituisce il numero di caratteri in una stringa,
> qual è l'espressione con gli indici che restituirà l'ultimo carattere della stringa `nome`?
> (N.B.: studieremo un modo più semplice di fare lo stesso in una lezione successiva.)
>
> > ## Soluzione
> >
> > `nome[len(nome) - 1]`
> {: .solution}
{: .challenge}

