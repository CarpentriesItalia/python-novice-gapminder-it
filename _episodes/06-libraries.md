---
title: "Librerie"
teaching: 10
exercises: 10
questions:
- "Come si fa a usare software scritto da altri?"
- "Come si fa a sapere a cosa serve un certo software?"
objectives:
- "Spiegare cosa sono le librerie di software e perché i programmatori le creano e le usano."
- "Scrivere programmi che importano e usano software della libreria standard di Python."
- "Trovare e leggere la documentazione delle librerie standard in modo interattivo (nell'interprete) e online."
keypoints:
- "Gran parte della forza di un linguaggio di programmazione consiste nelle sue librerie."
- "Un modulo di una libreria deve essere importato per essere usato."
- "Si usa `help` per scoprire il contenuto di un modulo di una libreria."
- "Per accorciare i programmi, si possono importare solo specifici elementi di una libreria."
- "Per accorciare i programmi, si può dare un alias a una libreria quando la si importa."
---
## Gran parte della forza di un linguaggio di programmazione consiste nelle sue librerie.

*   Una *libreria* è una collezione di file (chiamati *moduli*) che contiene
    funzioni scritte per essere usate da altri programmi.
    *   Può anche contenere dati (per esempio costanti numeriche) o altro.
    *   I contenuti di una libreria dovrebbero essere relativi a uno stesso tema, ma non c'è modo di garantirlo.
*   La [libreria standard][stdlib] di Python è un'estesa collezione di moduli che è sempre inclusa in Python stesso.
*   Moltissime librerie aggiuntive sono disponibili su [PyPI][pypi] (l'indice dei pacchetti di Python).
*   Vedremo come scrivere nuove librerie più avanti.

> ## Librerie e moduli
>
> Una libreria è una collezione di moduli, ma i due termini sono spesso usati come sinonimi,
> soprattutto perché molte librerie contengono un solo modulo; perciò, non preoccuparti se confondi le due cose.
{: .callout}


## Un modulo di una libreria deve essere importato per essere usato.

*   Si usa `import` per caricare un modulo di una libreria nella memoria di un programma.
*   Poi, ci si riferisce a un contenuto del modulo con `nome_modulo.nome_contenuto`.
    *   Python usa `.` per significare "parte di".
*   Usando `math`, uno dei moduli della libreria standard:

~~~
import math

print('pi greco è', math.pi)
print('cos(pigreco) è', math.cos(math.pi))
~~~
{: .language-python}
~~~
pi greco è 3.141592653589793
cos(pigreco) è -1.0
~~~
{: .output}

*   È necessario chiamare tutti gli elementi contenuti con il nome del modulo.
    *   `math.cos(pi)` non funziona, perché il riferimento a `pi`
        non ha modo di "ereditare" il riferimento a `math` della funzione.

## Si usa `help` per scoprire il contenuto di un modulo di una libreria.

*   Funziona esattamente come help per una funzione.

~~~
help(math)
~~~
{: .language-python}
~~~
Help on module math:

NAME
    math

MODULE REFERENCE
    http://docs.python.org/3/library/math

    The following documentation is automatically generated from the Python
    source files.  It may be incomplete, incorrect or include features that
    are considered implementation detail and may vary between Python
    implementations.  When in doubt, consult the module reference at the
    location listed above.

DESCRIPTION
    This module is always available.  It provides access to the
    mathematical functions defined by the C standard.

FUNCTIONS
    acos(x, /)
        Return the arc cosine (measured in radians) of x.
⋮ ⋮ ⋮
~~~
{: .output}

## Per accorciare i programmi, si possono importare solo specifici elementi di una libreria.

*   Si usa `from ... import ...` per caricare solo certi elementi specifici da un modulo di una libreria
*   Poi, ci si può riferire direttamente a questi senza usare il nome della libreria come prefisso.

~~~
from math import cos, pi

print('cos(pigreco) è', cos(pi))
~~~
{: .language-python}
~~~
cos(pigreco) è -1.0
~~~
{: .output}

## Per accorciare i programmi, si può dare un alias a una libreria quando la si importa.

*   Si usa `import ... as ...` per dare a una libreria un "soprannome" (*alias*) quando la si importa.
*   Poi, ci si riferisce ai membri della libreria usando il nome abbreviato.

~~~
import math as m

print('cos(pigreco) è', m.cos(m.pi))
~~~
{: .language-python}
~~~
cos(pigreco) è -1.0
~~~
{: .output}

*   Questo si fa normalmente per librerie che sono usate di frequente o hanno nomi lunghi.
    *   Ad esempio, la libreria per i grafici `matplotlib` è spesso abbreviata in `mpl`.
*   Tuttavia, questo può rendere i programmi più difficili da capire,
    poiché il lettore deve ricordarsi gli alias usati nel programma.

> ## Esplorare il modulo Math
>
> 1. Quale funzione del modulo `math` si potrebbe usare per calcolare una radice quadrata
>    *senza* usare `sqrt`?
> 2. Se questa funzione è presente nella libreria, perché esiste anche `sqrt`?
>
> > ## Soluzione
> > 1. Usando `help(math)` notiamo che c'è anche `pow(x,y)` oltre a `sqrt(x)`,
> >    pertanto possiamo usare `pow(x, 0.5)` per calcolare una radice quadrata.
> > 2. Si può dire che la funzione `sqrt(x)` sia più leggibile di `pow(x, 0.5)`
> >    scrivendo un'equzione. La leggibilità è una pietra angolare della buona programmazione,
> >    per cui ha senso avere una funzione specialmente per questo caso specifico comune.
> >
> >    Inoltre, la struttura della libreria `math` di Python ha le sue radici nello standard del C,
> >    che include sia `sqrt(x)` che `pow(x,y)`, pertanto un indizio della storia
> >    della programmazione emerge dai nomi delle funzioni di Python.
> {: .solution}
{: .challenge}

> ## Trovare il modulo giusto
>
> Immagina di voler scegliere un carattere a caso all'interno di una stringa:
>
> ~~~
> basi = 'ACTTGCTTGAC'
> ~~~
> {: .language-python}
>
> 1. Quale modulo della [libreria standard][stdlib] può aiutarti?
> 2. Che funzione sceglieresti all'interno di questo modulo? Ci sono diverse alternative?
> 3. Prova a scrivere un programma usando quella funzione.
>
> > ## Soluzione
> >
> > Il [modulo random][randommod] (funzioni casuali) sembra essere d'aiuto.
> >
> > La stringa ha 11 caratteri, ognuno dei quali ha un indice posizionale tra 0 e 10.
> > Puoi usare la funzione `random.randrange` (o il suo sinonimo `random.randint`
> > se lo trovi più facile da ricordare) per ottenere un intero casuale tra 0 e
> > 10, e poi scegliere il carattere corrispondente a quella posizione:
> >
> > ~~~
> > from random import randrange
> >
> > indice_casuale = randrange(len(basi))
> > print(basi[indice_casuale])
> > ~~~
> > {: .language-python}
> >
> > o anche, in maniera più compatta:
> >
> > ~~~
> > from random import randrange
> >
> > print(basi[randrange(len(basi))])
> > ~~~
> > {: .language-python}
> >
> > Forse avrai notato anche la funzione `random.sample`. Ci permette di essere
> > più sintetici:
> >
> > ~~~
> > from random import sample
> >
> > print(sample(basi, 1)[0])
> > ~~~
> > {: .language-python}
> >
> > Nota che questa funzione restituisce una lista di valori. Impareremo a usare le liste
> > nell'[episodio 11]({% link _episodes/11-lists.md %}).
> >
> > Ci sono anche altre funzioni che si potrebbero usare, ma ci costringerebbero a scrivere
> > codice più contorto.
> {: .solution}
{: .challenge}


> ## Esempio di programmazione: un puzzle (problema di Parson)
>
> Riordina le istruzioni seguenti in modo che una base di DNA casuale sia stampata
> insieme al valore del suo indice all'interno della stringa.  Non tutte le istruzioni sono
> necessariamente da usare. Aggiungi liberamente variabili intermedie se vuoi.
>
> ~~~
> basi = "ACTTGCTTGAC"
> import math
> import random
> ___ = random.randrange(n_basi)
> ___ = len(basi)
> print("base casuale ", basi[___], "indice della base", ___)
> ~~~
> {: .language-python}
>
> > ## Soluzione
> >
> > ~~~
> > import math 
> > import random
> > basi = "ACTTGCTTGAC" 
> > n_basi = len(basi)
> > idx = random.randrange(n_basi)
> > print("base casuale", bases[idx], "indice della base", idx)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Quando è disponibile aiuto?
>
> Quando un tuo collega scrive `help(math)`,
> Python dà un errore:
>
> ~~~
> NameError: name 'math' is not defined
> ~~~
> {: .error}
>
> Che cosa ha dimenticato di fare il tuo collega?
>
> > ## Soluzione
> >
> > Ha dimenticato di importare il modulo math (`import math`)
> {: .solution}
{: .challenge}

> ## Importare con gli alias
>
> 1. Riempi gli spazi vuoti in modo che il programma seguente stampi `90.0`.
> 2. Riscrivi il programma in modo che usi `import` *senza* `as`.
> 3. Quale delle due formi trovi sia più facile da leggere?
>
> ~~~
> import math as m
> angolo = ____.degrees(____.pi / 2)
> print(____)
> ~~~
> {: .language-python}
>
> > ## Soluzione
> >
> > ~~~
> > import math as m
> > angolo = m.degrees(m.pi / 2)
> > print(angolo)
> > ~~~
> > {: .language-python}
> >
> > può essere scritto anche
> >
> > ~~~
> > import math
> > angolo = math.degrees(math.pi / 2)
> > print(angolo)
> > ~~~
> > {: .language-python}
> >
> > Poiché hai appena scritto questo codice e lo conosci bene, potresti
> > trovare la prima versione più facile da leggere. Ma se leggessi un enorme programma
> > scritto da qualcun altro, o tornassi a leggere un enorme programma scritto da te
> > parecchi mesi più tardi, troveresti i nomi non abbreviati spesso più semplici, eccetto
> > laddove ci sono chiare convenzioni su come abbreviare.
> {: .solution}
{: .challenge}

> ## Ci sono molti modi di importare le librerie!
>
> Abbina le seguenti istruzioni `print` con il modo appropriato di importare la libreria.
>
> Istruzioni print:
>
> 1. `print("sin(pi/2) =", sin(pi/2))`
> 2. `print("sin(pi/2) =", m.sin(m.pi/2))`
> 3. `print("sin(pi/2) =", math.sin(math.pi/2))`
>
> Importazioni:
>
> 1. `from math import sin, pi`
> 2. `import math`
> 3. `import math as m`
> 4. `from math import *`
>
> > ## Soluzione
> >
> > 1. La libreria può essere importata nei modi 1 e 4. Per poter chiamare `sin` e `pi` senza
> >    il nome della libreria come prefisso, bisogna usare l'istruzione `from ... import ...`.
> >    L'importazione 1 importa specificamente le due funzioni
> >    `sin` and `pi`, l'importazione 4 importa tutte le funzioni del modulo `math`.
> > 2. L'importazione 3. Qui `sin` e `pi` sono chiamati con il nome abbreviato
> >    `m` anziché `math`. L'importazione 3 permette esattamente questo con la sintassi
> >    `import ... as ...`: crea l'alias `m` come forma abbreviata di `math`.
> > 3. L'importazione 2. Qui `sin` e `pi` sono chiamati attraverso il normale nome
> >    della libreria `math`, quindi basta la semplice chiamata `import ...`.
> {: .solution}
{: .challenge}

> ## Importare elementi specifici
>
> 1. Riempi gli spazi vuoti in modo che il programma seguente stampi `90.0`.
> 2. Trovi che questa versione sia più facile da leggere rispetto alle precedenti?
> 3. Qual è una possibile ragione per *non* usare sempre questa forma di `import`?
>
> ~~~
> ____ math import ____, ____
> angolo = degrees(pi / 2)
> print(angolo)
> ~~~
> {: .language-python}
>
> > ## Soluzione
> >
> > ~~~
> > from math import degrees, pi
> > angolo = degrees(pi / 2)
> > print(angolo)
> > ~~~
> > {: .language-python}
> >
> > Probabilmente troverai questa versione più facile da leggere, visto che è meno disordinata.
> > La ragione principale per non usare questo modo di importare è quando si vogliono evitare conflitti di nomi.
> > Per esempio, non puoi importare `degrees` in questo modo quando vuoi anche
> > usare il nome `degrees` per una variabile o una funzione scritta da te, o se
> > ti serve anche importare una funzione chiamata `degrees` da un'altra libreria.
> {: .solution}
{: .challenge}

> ## Leggere i messaggi di errore
>
> 1. Leggi il codice seguente e cerca di identificare gli errori senza eseguirlo.
> 2. Esegui il codice, e leggi il messaggio di errore. Che tipo di errore è?
>
> ~~~
> from math import log
> log(0)
> ~~~
> {: .language-python}
>
> > ## Soluzione
> >
> > 1. Il logaritmo di `x` è definito solo per `x > 0`, pertanto 0 è al di fuori del
> >    dominio della funzione.
> > 2. Si ottiene un errore di tipo "ValueError", che indica che la funzione
> >    ha ricevuto un valore inadatto in uno dei suoi argomenti. Il messaggio aggiuntivo
> >    "math domain error" chiarifica qual è il problema.
> {: .solution}
{: .challenge}

[pypi]: https://pypi.python.org/pypi/
[stdlib]: https://docs.python.org/3/library/
[randommod]: https://docs.python.org/3/library/random.html

