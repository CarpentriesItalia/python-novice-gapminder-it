---
title: "Lanciare e chiudere Python"
teaching: 15
exercises: 0
questions:
- "Come lanciare un programma in Python?"
objectives:
- "Lanciare il server JupyterLab." 
- "Creare un nuovo script Python." 
- "Creare un Jupyter notebook."
- "Spegnere il server JupyterLab."
- "Capire la differenza tra un programma Python e un Jupyter notebook."
- "Creare celle Markdown in un Jupyter notebook."
- "Creare ed eseguire celle Python in un notebook."
keypoints:
- "Gli script in Python sono file di testo semplice."
- "Usare il Jupyter Notebook per scrivere ed eseguire codice Python."
- "Il Notebook ha le modalità Comando e Modifica."
- "Usare la tastiera e il mouse per selezionare e modificare celle."
- "Il Notebook può convertire codice Markdown in una documentazione curata."
- "Il Markdown è in grado di fare la maggior parte di ciò che si può fare con l'HTML."
---

## Iniziare a usare JupyterLab

Molti sviluppatori di software usano un ambiente di sviluppo integrato
(IDE, integrated development environment) oppure un editor di testo per creare e modificare i loro programmi in Python.
In questa lezione, noi useremo [JupyterLab][jupyterlab].

JupyterLab è un'applicazione con un'interfaccia utente basata sul browser web, creata dal [Project Jupyter][jupyter],
che ci permette di lavorare con documenti e strumenti come Jupyter notebook, editor di testo, terminali, e anche componenti personalizzate,
in modo flessibile, integrato, ed espandibile. JupyterLab richiede un browser relativamente aggiornato (se possibile, una versione recente di Chrome, Safari o Firefox);
Internet Explorer 9 e precedenti *non* sono supportati.

JupyterLab è già incluso nella distribuzione di Python chiamata Anaconda. Se non hai già installato la
distribuzione Anaconda Python, leggi le [istruzioni di setup] ({{ page.root }}/setup/) per sapere come installarla.

Sebbene JupyterLab sia un'applicazione a cui si accede dal browser web, JupyterLab è un software
che gira localmente, sul tuo calcolatore, e non richiede una connessione a internet.
* Il server JupyterLab invia comunicazioni al tuo browser web.
* Il server JupyterLab esegue il lavoro, e il browser visualizza il risultato.
* Quando scriverai codice nel browser, vedrai il risultato non appena la pagina web comunica con il server JupyterLab.

> ## JupyterLab? E allora i Jupyter notebook cosa sono?
> 
> JupyterLab è [lo stadio evolutivo successivo al Jupyter Notebook](https://jupyterlab.readthedocs.io/en/stable/getting_started/overview.html#overview). Se hai già avuto
> occasione di lavorare con il Jupyter notebook, allora hai già un'idea di cosa aspettarti
> da JupyterLab. 
> 
> Chi ha già una buona conoscenza del Jupyter notebook ed è interessato in una discussione più approfondita sulle somiglianze e differenze
> tra le interfacce utente di JupyterLab e del Jupyter notebook, può trovare maggiori informazioni nella
> [documentazione dell'interfaccia utente JupyterLab][jupyterlab-ui].
{: .callout}

## Lanciare JupyterLab

### Mac OS X
Per far partire il server JupyterLab, è necessario avere accesso alla linea di comando, attraverso il Terminale.
Ci sono due modi per aprire il Terminale sul Mac.

1. Nella cartella Applicazioni, apri Utilities/Utilità, e fai doppio clic su Terminale.
2. Press <kbd>Comando</kbd> + <kbd>barra spaziatrice</kbd> per aprire Spotlight. Digita `Terminale` e
e fai doppio clic sul risultato della ricerca, o premi <kbd>Invio</kbd>

Una volta aperto il terminale, scrivi il comando che fa partire il server JupyterLab.

~~~
$ jupyter lab
~~~
{: .bash}

### Per utenti Windows
Per far partire il server JupyterLab, è necessario aprire Anaconda Prompt.

Premi <kbd>Tasto Windows</kbd> e cerca `Anaconda Prompt`, clicca sul risultato o premi Invio.

Dopo aver aperto Anaconda Prompt, scrivi il comando:

~~~
$ jupyter lab
~~~
{: .bash}

Qui sotto, uno screenshot della pagina iniziale di JupyterLab, simile a quella che dovrebbe aprirsi sul
tuo browser predefinito dopo aver lanciato il server JupyterLab, sia su Mac OS X sia su Windows.

<p align='center'>
  <img alt="JupyterLab landing page" src="../fig/0_jupyterlab_landing_page.png" width="750"/>
</p>

## L'interfaccia JupyterLab

JupyterLab ha molte caratteristiche simili a quelle degli ambienti di sviluppo integrato (IDE) più tradizionali,
ma è specializzato nel costruire moduli adattabili, per programmi interattivi ed esplorativi.

L'[interfaccia JupyterLab](https://jupyterlab.readthedocs.io/en/stable/user/interface.html) consiste in una
barra del menù, una barra laterale sinistra (che può essere nascosta), e nell'area di lavoro principale, che
contiene diverse schede con documenti e attività. 

### Barra del menù

La barra del menù nella parte alta di JupyterLab ha menù principali che mostrano le varie azioni
disponibili in JupyterLab, insieme alle loro scorciatoie da tastiera (laddove esistono). I menù
seguenti sono predefiniti.

*   **File:** Azioni relative ai file e alle cartelle, come *New* (nuovo), *Open* (apri), *Close* (chiudi), *Save* (salva), ecc. Il menù *File* contiene anche l'azione *Quit* (esci), usata per spegnere il server JupyterLab.
*   **Edit:** Azioni relative alla modifica dei documenti, e altre simili, come *Undo* (annulla), *Cut* (taglia), *Copy* (copia), *Paste* (incolla), ecc.
*   **View** (vista): azioni che modificano l'aspetto di JupyterLab. 
*   **Run:** Azioni per eseguire il codice nelle diverse "attività", come i notebook e le console (spiegate più sotto).
*   **Kernel:** Azioni per la gestione dei kernel, che, come detto sopra, sono processi tra loro separati che eseguono il codice.
*   **Tabs:** La lista dei documenti e delle attività aperte nel pannello dock.
*   **Settings:** le impostazioni più comuni di JupyterLab possono essere configurate usando questo menù. C'è anche un'opzione "Advanced Settings Editor" nel menù a tendina, che serve per un controllo più preciso delle impostazioni e configurazioni di JupyterLab.
*   **Help:** Una lista di link di aiuto su JupyterLab e sui kernel.

Qui sotto, uno screenshot della barra dei menù predefinita.

<p align='center'>
    <img alt="JupyterLab Menu Bar" src="../fig/0_jupyterlab_menu_bar.png" width="750"/>
</p>

### Barra laterale sinistra

La barra laterale sinistra contiene diverse schede usate di frequente, come il navigfatore dei file
(che mostra i contenuti della cartella in cui il server JupyterLab è stato lanciato), una lista dei kernel e
dei terminali attualmente attivi, la palette dei comandi, e una lista delle schede aperte nell'area di lavoro
principale. Qui sotto è mostrato uno screenshot della barra laterale sinistra predefinita.

<p align='center'>
    <img alt="JupyterLab Left Side Bar" src="../fig/0_jupyterlab_left_side_bar.png" width="250"/>
</p>

La barra laterale sinistra può essere nascosta o mostrata selezionando "Show Left Sidebar" nel menù View
o cliccando sull'icona della scheda attiva al momento.

### Area di lavoro principale

L'area di lavoro principale di JupyterLab consente di gestire i documenti (notebook, file di testo, ecc.)
e le altre attività (i terminali, le console del codice, ecc.), sistemandoli in pannelli di schede che possono
essere ridimensionati o suddivisi. Qui sotto è mostrato uno screenshot della barra del menù predefinita.

<p align='center'>
    <img alt="JupyterLab Main Work Area" src="../fig/0_jupyterlab_main_work_area.png" width="750"/>
</p>

Per spostare una scheda in un pannello, trascina la scheda verso il centro di un pannello di schede.
Per suddividere un pannello di schede, trascina una scheda alla sinistra, alla destra, o sopra o sotto al
pannello. L'area di lavoro ha sempre una sola attività corrente. La scheda corrispondente a questa attività
è identificato da un bordo superiore colorato (blu è il colore predefinito).

## Creare uno script in Python

*   Per iniziare a scrivere un nuovo programma in Python, clicca sull'icona Text File (file di testo) sotto l'intestazione *Other* (altro), nella scheda Launcher dell'area di lavoro principale.
    *   In alternativa, si può anche creare un nuovo file di testo selezionando *New -> Text File* dal menù  *File* nella barra dei menù.
*   Per convertire questo file di testo semplice in un programma Python, seleziona l'azione *Save File As* (salva come) dal menù *File* nella barra dei menù, e dai al tuo nuovo file di testo un nome che termina con l'estensione `.py`.
    *   L'estensione `.py` rende noto a tutti (incluso il sistema operativo) che questo file di testo è un programma in Python.
    *   Questa non è una condizione necessaria, ma una convenzione.

## Creare un Jupyter Notebook

Per aprire un nuovo notebook, clicca sull'icona Python 3 sotto l'intestazione *Notebook* della scheda
Launcher nell'area di lavoro principale. Si può creare un notebook anche selezionando *New -> Notebook* dal menù *File* nella barra dei menù.

Altre informazioni sui Jupyter notebook.

  *   I notebook sono file con l'estensione `.ipynb`, in modo che si possano distinguere dai programmi Python in formato testo semplice.
  *   I notebook possono essere esportati in script Python che possono poi essere eseguiti da linea di comando.

Qui sotto, è mostrato uno screenshot di un Jupyter notebook attivo all'interno di JupyterLab. Se ti
interessano altri dettagli, vedi la [documentazione ufficiale dei notebook][jupyterlab-notebook-docs].

<p align='center'>
    <img alt="Example Jupyter Notebook" src="../fig/0_jupyterlab_notebook_screenshot.png" width="750"/>
</p>

> ## Come funziona il formato notebook
>
> *   I file notebook sono salvati in un formato chiamato JSON.
> *   Proprio come per una pagina web, ciò che è salvato ha un aspetto diverso da ciò che è mostrato nel browser.
> *   Tuttavia, questo formato permette a Jupyter di mescolare codice sorgente, testo e immagini in uno stesso file.
{: .callout}

> ## Disporre documenti in pannelli di schede
>
> Nell'area di lavoro principale di JupyterLab, si possono disporre i documenti in pannelli di schede.
> Ecco un esempio dalla [documentazione ufficiale][jupyterlab].
> 
> <p align='center'>
>    <img alt="Multi-panel JupyterLab" src="../fig/0_multipanel_jupyterlab_screenshot.png" width="750"/>
> </p>
>
> Innanzitutto, crea un file di testo, una console Python e una finestra di terminale, e sistemale in tre
> pannelli nell'area di lavoro principale. Poi, crea un notebook, una finestra di terminale e un file di
> testo, e sistemali in tre pannelli nell'area di lavoro principale. Infine, crea una combinazione a scelta
> di pannelli e schede. Qual è la combinazione di pannelli e schede che pensi ti sarà più utile per il
> tuo flusso di lavoro?
>
> > ## Soluzione
> >
> > Dopo aver creato le schede necessarie, puoi trascinarne una al centro di un pannello per spostare
> > la scheda nel pannello; poi, puoi suddividere un pannello trascinando una scheda verso sinistra,
> > verso destra, verso l'alto o verso il basso all'interno del pannello.
> {: .solution}
{: .challenge}

## Usare il Jupyter Notebook per scrivere e eseguire codice Python.

*   Sebbene sia comune scrivere script in Python usando un editor di testo, per questo corso useremo [Jupyter Notebook][jupyter] da qui in avanti.
*   Ci sono diversi vantaggi:
* È facile digitare, modificare, copiare e incollare blocchi di codice.
* L'autocompletamento (premendo il tasto *tab*) permette di visualizzare facilmente i nomi degli elementi in uso
        e di saperne di più.
    *   Permette di annotare il codice con link, testo di dimensioni diverse, elenchi puntati, ecc.
        per renderlo più facilmente comprensibile a te e ai tuoi collaboratori.
    *   Ti permette di mostrare le figure insieme al codice che le genera,
        così da dare una narrazione completa delle tue analisi.
*   Ogni notebook contiene una o più celle con codice, testo o immagini.

> ## Distinguere codice e testo
>
> Jupyter mescola codice e testo in blocchi di tipo diverso, chiamate celle. In genere, usiamo il termine
> "codice" nel senso di "codice sorgente di un software, scritto in un linguaggio come Python".
> Una "cella di codice" ("code cell") in un Notebook è una cella che contiene software;
> una "cella di testo" ("text cell"), al contrario, contiene prosa ordinaria, scritta per essere letta da umani.
{: .callout}

## Il Notebook ha le modalità Comando e Modifica.

*   Premendo <kbd>Esc</kbd> e <kbd>Invio</kbd> in alternanza, il bordo esterno di una cella di codice cambia da grigio a blu.
*   Queste sono le modalità **Comando** (grigio) e **Modifica** (blu) del notebook.
*   La modalità Comando consente di agire su proprietà globali del notebook, mentre la modalità Modifica cambia i contenuti della cella.
*   Quando in modalità Comando (esc/grigio),
    *   Il tasto <kbd>b</kbd>crea una nuova cella al di sotto di quella attualmente selezionata. 
    *   Il tasto <kbd>a</kbd> ne crea una al di sopra.
    *   Il tasto <kbd>x</kbd> elimina la cella selezionata.
    *   Il tasto <kbd>z</kbd> annulla la tua ultima operazione sulle celle (come l'eliminazione o creazione di una cella, ecc.).
*   Tutte queste azioni possono essere svolte anche usando i menù, ma ci sono molte scorciatoie da tastiera per rendere le operazioni più rapide.

> ## La differenza tra modalità Comando e Modifica
>
> Nella tua pagina Jupyter Notebook, ti trovi in modalità Comando o Modifica, al momento?
> Passa da una modalità all'altra. 
> Usa le scorciatoie da tastiera per creare una nuova cella. 
> Usa le scorciatoie per eliminare una cella.
> Usa le scorciatorie per annullare la tua ultima operazione.
>
> > ## Soluzione
> >
> > La modalità Comando ha un contorno grigio, mentre Modifica ha un contorno blu.
> > Usa <kbd>Esc</kbd> e <kbd>Invio</kbd> per passare da una all'altra. 
> > Assicurati di essere in modalità Comando (Premi <kbd>Esc</kbd> se la cella è blu).  Digita <kbd>b</kbd> oppure <kbd>a</kbd>.
> > Assicurati di essere in modalità Comando (Premi 3Esc3 se la cella è blu).  Digita <kbd>x</kbd>.
> > Assicurati di essere in modalità Comando (Premi 3Esc3 se la cella è blu).  Digita <kbd>z</kbd>.
> {: .solution}
{: .challenge}

### Usare tastiera e mouse per selezionare e modificare celle.

*   Premendo<kbd>Invio</kbd>, il bordo della cella diventa blu, e la modalità Modifica è attiva, permettendo
    di scrivere all'interno della cella.
*   Poiché vogliamo poter scrivere più di una riga di codice in ogni cella,
    premere il tasto <kbd>Invio</kbd> in modalità Modifica muove il cursore alla riga sucessiva 
    all'interno della cella, come in un editor di testo.
*   Per comunicare al Notebook che vogliamo eseguire il codice presente nella cella, dobbiamo usare un altro metodo.
*   Premendo <kbd>Shift</kbd>+<kbd>Invio</kbd>insieme, il computer esegue il contenuto della cella. 
*   Notare che il tasto <kbd>Invio</kbd> e il tasto <kbd>Shift</kbd> di destra sono uno accanto all'altro
    sulla tastiera.

### Il Notebook converte codice Markdown in documentazione graficamente curata.

*   Il notebook può anche visualizzare [Markdown][markdown].
    *   Un formato di testo semplice, usato per scrivere liste, link,
        e altri elementi come in una pagina web.
    *   In altre parole, un sottoinsieme dell'HTML simile a quello che si può mandare in una cara, vecchia, email.
*   Per trasformare la cella selezionata in una cella Markdown, entra in modalità Comando
     (<kbd>Esc</kbd>/grigio) e premi il tasto <kbd>M</kbd> .
*   `In [ ]:` scompare, indicando che non è più una cella di codice, e si può usare per scrivere Markdown.
*   Per trasformare la cella selezionata in una cella di codice, entra in modalità Comando
     (<kbd>Esc</kbd>/grigio) e premi il tasto <kbd>Y</kbd> .

### Il Markdown permette di fare molte cose tipiche dell'HTML.

<div class="row">
  <div class="col-md-6" markdown="1">
~~~
*   Usa degli asterischi
*   per creare
*   elenchi puntati.
~~~
  </div>
  <div class="col-md-6" markdown="1">
*   Usa degli asterischi
*   per creare
*   elenchi puntati.
  </div>
</div>

<div class="row">
  <div class="col-md-6" markdown="1">
~~~
1.  Usa dei numeri
1.  per creare
1.  elenchi numerati.
~~~
  </div>
  <div class="col-md-6" markdown="1">
1.  Usa dei numeri
1.  per creare
1.  elenchi numerati.
  </div>
</div>

<div class="row">
  <div class="col-md-6" markdown="1">
~~~
*  Usa l'indentazione
\t*  Per creare sotto-elenchi 
\t*  dello stesso tipo
*  Oppure
\t1. Di un altro
\t1. tipo
~~~
  </div>
  <div class="col-md-6" markdown="1">
* Usa l'indentazione
* Per creare sotto-elenchi 
\t* dello stesso tipo
* Oppure
\t1. Di un altro
\t1. tipo
  </div>
</div>

<div class="row">
  <div class="col-md-6" markdown="1">
~~~
# Un titolo di primo livello
~~~
  </div>
  <div class="col-md-6" markdown="1">
# Un titolo di primo livello
  </div>
</div>

<div class="row">
  <div class="col-md-6" markdown="1">
~~~
## Un titolo di secondo livello (ecc.)
~~~
  </div>
  <div class="col-md-6" markdown="1">
## Un titolo di secondo livello (ecc.)
  </div>
</div>

<div class="row">
  <div class="col-md-6" markdown="1">
~~~
La presenza di ritorni a capo
non ha importanza.

Ma righe lasciate vuote
danno luogo a un nuovo paragrafo.
~~~
  </div>
  <div class="col-md-6" markdown="1">
La presenza di ritorni a capo
non ha importanza.

Ma righe lasciate vuote
danno luogo a un nuovo paragrafo.
  </div>
</div>

<div class="row">
  <div class="col-md-6" markdown="1">
~~~
Per [creare link](http://software-carpentry.org) si scrive `[...](...)`.
O si possono usare [link nominali][data_carpentry].

[data_carpentry]: http://datacarpentry.org
~~~
  </div>
  <div class="col-md-6" markdown="1">
Per [creare link](http://software-carpentry.org) si scrive `[...](...)`.
O si possono usare [link nominali][data_carpentry].

[data_carpentry]: http://datacarpentry.org
  </div>
</div>

> ## Creare elenchi in Markdown
>
> Crea una lista in Markdown con questo aspetto:
>
> 1.  Ottenere finanziamenti.
> 2.  Lavorare.
>     *   Progettare gli esperimenti.
>     *   Raccogliere dati.
>     *   Analizzarli.
> 3.  Scrivere il resoconto.
> 4.  Pubblicare.
> 
> > ## Soluzione
> >
> > Questo esercizio contiene sia elenchi puntati sia numerati. 
> > Notare che l'elenco puntato è indentato di due spazi in modo da essere allineato con gli elementi dell'elenco numerato.
> > ~~~
> > 1. Ottenere finanziamenti.
> > 2. Lavorare.
> > * Progettare gli esperimenti.
> > * Raccogliere dati.
> > * Analizzarli.
> > 3. Scrivere il resoconto.
> > 4. Pubblicare.
> > ~~~
> {: .solution}
{: .challenge}

> ## Ancora matematica
>
> Quando si esegue una cella di codice Python che contiene
> diversi calcoli, cosa viene mostrato come risultato?
> Per esempio, cosa succede quando eseguiamo questa cella?
>
> ~~~
> 7 * 3
> 2 + 1
> ~~~
> {: .language-python}
> 
> > ## Soluzione
> >
> > Python ci mostra solo il risultato dell'ultimo calcolo.
> > ~~~
> > 3
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Cambiare una cella esistente da Codice a Markdown
>
> Cosa succede se si scrive Python in una cella di codice,
> e poi la si cambia in una cella Markdown?
> Per esempio,
> scrivi il codice seguente in una cella di codice:
>
> ~~~
> x = 6 * 7 + 12
> print(x)
> ~~~
> {: .language-python}
>
> Poi eseguila con <kbd>Shift</kbd>+<kbd>Invio</kbd> per accertarti che funzioni come cella di codice.
> Ora, torna indietro e usa <kbd>Esc</kbd> seguito da <kbd>m</kbd> per convertirla in una cella Markdown
> e "eseguila" con <kbd>Shift</kbd>+<kbd>Invio</kbd>.
> Cosa è successo? In che modo il risultato può essere utile?
> 
> > ## Soluzione
> >
> > Il codice Python viene trattato come testo Markdown.
> > Le righe appaiono come un paragrafo unico.
> > Può essere utile per "attivare" e "disattivare" alcune celle, in notebook che sono usati per scopi diversi.
> > ~~~
> > x = 6 * 7 + 12 print(x)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Equazioni
>
> Standard Markdown (l'implementazione di Markdown usata in queste note) non è in grado di visualizzare equazioni,
> ma il notebook può.
> Crea una nuova cella Markdown
> e inserisci quanto segue:
>
> ~~~
> $\sum_{i=1}^{N} 2^{-i} \approx 1$
> ~~~
>
> (Potrebbe essere più comodo copiare e incollare.)
> Che cosa mostra?
> A cosa pensi servano il trattino basso, `_`, l'accento circonflesso, `^` e il simbolo del dollaro, `$`?
> 
> > ## Soluzione
> >
> > Il notebook ci mostra l'equazione interpretata come sintassi di equazione LaTeX.
> > Il simbolo del dollaro, `$`, si usa per dire all'interprete Markdown che il contenuto è un'equazione LaTeX.
> > Se non conosci LaTeX,  il trattino basso, `_`, si usa per i pedici, e il circonflesso, `^`, si usa per gli apici.
> > Una coppia di parentesi graffe, `{` and `}`, si usa per raggruppare elementi assieme, in modo che `i=1` sia tutto un pedice, e `N` sia l'apice.
> > Analogamente, `-i` è in parentesi graffe in modo che tutta l'espressione sia l'esponente di `2`.
> > `\sum` e `\approx` sono comandi LaTeX per i simboli di sommatoria e di "approssimativamente". 
> {: .solution}
{: .challenge}

## Chiudere JupyterLab

*   Dalla barra dei menù, seleziona il menù "File" e scegli "Quit" (esci) in fondo al menù a comparsa. Ti verrà chiesto di confermare che vuoi spegnere il server JupyterLab (non dimenticare di salvare il lavoro fatto!). Clicca su "Confirm" (conferma) per spegnere il server JupyterLab.
*   Per riaccendere un server JupyterLab, sarà necessario dare nuovamente il comando seguente in una shell.

~~~
$ jupyter lab
~~~

> ## Chiudere JupyterLab
>
> Esercitati a chiudere e riaprire il server JupyterLab.
{: .challenge}
[anaconda]: https://docs.continuum.io/anaconda/install
[jupyterlab-ui]: https://jupyterlab.readthedocs.io/en/stable/user/interface.html
[jupyterlab-notebook-docs]: https://jupyterlab.readthedocs.io/en/stable/user/notebook.html
[markdown]: https://en.wikipedia.org/wiki/Markdown

