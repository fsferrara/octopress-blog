---
title: Early development of Artificial Intelligence
layout: post
comments: true
categories:
  - history
tags:
  - ai
  - artificial-intelligence
  - computer-science
  - turing
---
Primi sviluppi dell&#8217;Intelligenza Artificiale.

E&#8217; difficile dare una definizione di Intelligenza Artificiale (IA) in quando essa è vista sia dal punto di vista ingegneristico (che punta a costruire macchine intelligenti per assistere l&#8217;uomo), sia dal punto di vista psicologico (che punta a riprodurre nelle macchine le caratteristiche dell&#8217;attività cognitiva umana).

Seppur con idee diverse, i pionieri dell&#8217;IA (McCarthy, Minsky, Rochesterm, e Shannon) videro nel calcolatore digitale uno strumento con capacità di elaborazione ineguagliate, quindi uno strumento adatto al confronto con alcuni aspetti della mente umana.

Si cominciarono a sviluppare i primi programmi relativi ad ambiti ben delimitati in cui c&#8217;erano  solo regole esplicite per l&#8217;elaborazione simbolica e poca conoscenza specializzata. Motivo di questo inizio era la scarsa capacità di memoria e di calcolo dei calcolatori di quei tempi.

Successivamente si parte con lo sviluppo di sistemi esperti, dove la conoscenza specializzata nel campo ci porta ad avere buone prestazioni.

La diffusione di queste tecniche di IA ci conferma il successo dal punto di vista ingegneristico, ma cosa possiamo dire dal punto di vista psicologico?

Cosa implica la costruzione di macchine che riproducono caratteristiche essenziali dell&#8217;attività umana? Dove si colloca l&#8217;IA nell&#8217;ambito delle ricerche sul sistema cervello-mente che coinvolgono le neuroscienze e la psicologia?

<!--more-->

## Turing e la Macchina di Turing Universale

Abbinando le MdT (Macchine di Turing) alle codifiche di Godel, nasce un modo di codificare le MdT. Si ha inoltre un _procedimento effettivo_ per la codifica e la decodifica.

Dalle MdT codificate, Turing arriva alla macchina universale, che è una particolare MdT che, accettando in input la descrizione di una qualsiasi MdT, riesce a comportarsi come essa.

Dalla **MdT Universale** nasce la nozione di **Macchina Programmabile**.

Da questa considerzione ci si chiese se le macchine possano essere intelligenti. Su questo Turing scrive l&#8217;articolo &#8220;Macchine calcolatrici e intelligenza&#8221;.

## Macchine calcolatrici e intelligenza

Turing considera la domanda: &#8220;_Possono pensare le macchine?_&#8220;. In questa domanda i termini **macchina** e **pensare** non sono di facile definizione.

Possiamo definire la parola **macchina** possiamo imporre che la macchina sia composta da tre parti: memoria, unità operativa, e governo; dove la memoria è un deposito di informazioni, l&#8217;unità operativa è la parte atta ad eseguire operazioni, ed il governo coordina l&#8217;unità operativa e la memoria.

Quindi scendendo più in dettaglio riusciamo a definire cos&#8217;è una macchina.

Cosa possiamo invece definire la parola **pensare**? Turing non riesce a farlo.

Per questo pensa di riformulare la domanda &#8220;_Possono pensare le macchine?_&#8221; con un&#8217;altra. Riformula il problema in termini di un gioco dove si trovano tre persona A (un uomo), B (una donna), e C (un&#8217;interrogante). C è isolato in una stanza, e può comunicare con A e B mediante messaggi di tipo linguistico.

Lo scopo di C, che parla con due individui, è di capire chi è la donna e chi è l&#8217;uomo. B (che è la donna) ha il compito di aiutare l&#8217;interrogante C, mentre lo scopo di A (l&#8217;uomo) è quello di ingannarlo.

La domanda riformulata è: &#8220;_Che cosa accadrà se una macchina prende il posto di A nel gioco? La frequenza delle risposte errate da parte di C sarà la stessa di quando il gioco si svolge tra uomini?_&#8220;.

Chiamiamo questo **Test di Turing**.

### Test di Turing e Intelligenza

Superare il test di Turing, non è una condizione né necessaria, né sufficiente per stabilire se un individuo o una macchina è intelligente.

  * Condizione Necessaria: se un essere è intelligente deve necessariamente superare il Test di Turing. Ma ci sono situazioni, come quelle delle persone nello stato locked-in (ad esempio il famoso caso di Piergiorgio Welby), in cui l&#8217;individuo non è in grado di superare il test, ma comunque non possiamo dire che tale individuo non è intelligente.
  * Condizione Sufficiente: supponiamo una macchina con un programma complicatissimo, che è fatta apposta per superare il Test di Turing. Questa macchina sa solo superare questo test e basta: possiamo definirela intelligente?

Quindi il superamento del Test di Turing da parte di una macchina non è né condizione necessaria, né condizione sufficiente per affermare che la macchina stressa sia intelligente.

### Osservazioni all&#8217;articolo

<span style="text-decoration: underline;">Prima Osservazione: Funzionalismo</span>

Notiamo che in questo gioco la macchina da risposte di tipo linguistico; infatti Turing divide nettamente le capacità fisiche di un essere umano, dalle capacità intellettuali (o mentali). Questo non è vero nell&#8217;eccezione Darwiniana in cui le capacità mentali di un essere vivente sono di fondamentale importanza per coordinare le capacità motorie, e permettono così di sopravvivere.

Essendo la mente umana composta da materiali diversi da quelli con i quali è costruita una macchina, Turing adotta il funzionalismo, ossia paragona il funzionamento degli oggetti anche se costruiti in modo diverso.

<span style="text-decoration: underline;">Seconda Osservazione: La mente funziona a stati discreti</span>

I calcolatori digitali sono indubbiamente delle macchine a _stati discreti_. Ovvero si muovono a scatti improvvisi ben distinguibili l&#8217;uno dall&#8217;altro.

Anche se in realtà in natura niente è discreto; se indaghiamo un calcolatore digitale funziona anch&#8217;esso in modo _continuo_. Ma consideriamolo una macchina a stati discreti.

_Ci conviene discretizzare la mente paragonandola ad un calcolatore digitale_?

<span style="text-decoration: underline;">Terza Osservazione: I calcolatori digitali non sono caotici</span>

Dato un input in ingresso ad una macchina riusciamo a predire tutti i suoi stati, ed il suo output, in modo esatto. Nel mondo invece vige la teoria del caos, nella quale piccole variazioni nelle condizioni iniziali producono grandi variazioni nel comportamento a lungo termine di un sistema. Ad esempio il battito d&#8217;ali di una farfalla può essere la causa di un uragano dall&#8217;altra parte del mondo.

### Obiezioni Contrarie all&#8217;argomento principale dell&#8217;articolo

<span style="text-decoration: underline;">Obiezione Teologica:</span> &#8220;Solo Dio ha il potere di creare esseri pensanti&#8221;.

Questa obiezione pone serie restrizioni alla provvidenza divina: chi ci dice che Dio non ci abbia dato il potere di creare macchine pensanti?

<span style="text-decoration: underline;">Obiezione della Testa nella Sabbia:</span> Questa è l&#8217;obiezione di chi ha paura delle macchine pensanti. A queste persone piace sentirsi superiori di ogni altra cosa, e si sentono minacciati da questo tentativo di creare macchine pensanti.

<span style="text-decoration: underline;">Obiezione Matematica:</span> I teoremi di incompletezza di Godel, ed altri risultati ad esso annessi, dimostrano che le macchine non possono conoscere tutte le verità. Quindi esistono dei limiti, e si sostiene che la mente umana non abbia questi limiti.

Ma non è giusto condannare così i calcolatori; diamo risposte errate anche noi. Inoltre ci possono essere uomini più abili di una macchina, ma possono essere costruite altre macchine più abili di questi uomini. Quindi non ci possono essere uomini più abili di tutte le macchine.

<span style="text-decoration: underline;">Obiezione dell&#8217;Autocoscienza</span>: Possiamo dividere la coscienza in &#8220;essere consapevole del proprio stato&#8221;, ed &#8220;essere consapevoli di provare&#8221;. Possiamo costruire macchine con medoti di **Machine Learning** che sono consapevoli del proprio stato, ma non ancora riusciamo ad immaginare macchine che sappiano provare dei sentimenti.

<span style="text-decoration: underline;">Obiezioni basate su incapacità varie</span>: ad esempio una macchina è capace di gustare le fragole con la panna.

Queste obiezioni nascono dal fatto che vogliamo far assomigliare le macchine agli essere umani. Ma, non essendo le macchine degli essere umani, è difficile avere un rapporto di amicizia tra un uomo ed una macchina.

<span style="text-decoration: underline;">Obiezione di Lady Lovelace:</span> &#8220;La macchina può eseguire solo quello che gli diciamo di fare!&#8221;. Questa obiezione è vecchia e risale ai tempi della macchina universale di Babbage.

Con i moderni metodi di **Machine Learning** possiamo avere delle macchine che riescono ad apprendere, anche se sono formate da un nucleo di base non modificabile. Quindi anche essendo una macchina _deterministica_, possiamo avere macchine che modificano il proprio comportamento man mano che apprendono nuove regole.

<span style="text-decoration: underline;">Obiezione fondata sulla continuità del sistema nervoso:</span> Ancora una volta ci rifacciamo al concetto di funzionalismo, secondo il quale cerchiamo di ottenere solo un comportamento intelligente, e non pretendiamo che internamente le cose funzionino allo stesso modo.

### Possono le macchine pensare?

Dopo l&#8217;articolo di Turing partono gli studi per costruire macchine in grado di competere con l&#8217;uomo in ambiti intellettuali. Ma quel&#8217;è la strada migliore per iniziare a costruire queste macchine?

L&#8217;_IA_ comincia a sviluppare programmi per calcolatori digitali capaci di svolgere attività molto astratte, come giocare a scacchi.

La _robotica_ invece inizia mettendo in risalto il comportamento intelligente degli esseri viventi, e comincia a costruire dispositivi meccanici che si comportano in modo intelligente.

Parallelamente a queste due nasce anche la branca della **Machine Learning**, un&#8217;intuizione geniale da parte di Turing.

## La cibernetica prima dei calcolatori digitali

La cibernetica nasce con i sistemi a retroazione. La differenza con il punto di vista di Turing, è che questa volta <span style="text-decoration: underline;">il comportamento intelligente è visto come un comportamento flessibile-adattativo all&#8217;ambiente</span>: c&#8217;è un tentativo di collegare questi sistemi a retroazione ai sistemi biologici, con un conseguente collegamento alla scienza molto più forte.

Da un altro punto di vista notiamo che i cibernetici partono dal basso, costruendo prima sistemi molto semplici, mentre Turing punta a riprodurre l&#8217;attività mentale umana con un macchina&#8230; un compito arduo.

Un primo esempio di sistema a retroazione è la valvola di sfiato della caldaia di una locomotiva a vapore; il suo compito era quello di tenere la pressione costante all&#8217;interno della caldaia, in modo da mantenere costante la velocità del treno. Quindi quando la pressione era troppo alta, la valvola faceva uscire del vapore per farla diminuire.

Questo primo meccanismo di sistema a retroazione puntava a correggere l&#8217;errore, in un ciclo di questo tipo:

  1. Osservare l&#8217;output del sistema
  2. Misurare l&#8217;errore
  3. Apportare le modifiche atte a correggere l&#8217;errore

Questi meccanismi hanno delle caratteristiche in comune con i sistemi biologici: ad esempio il corpo umano ha un meccanismo simile per controllare la temperatura corporea (la sudorazione).

Rosenblueth, Wiener, e Bigelow, nel loro articolo &#8220;_Coportamento, Scopo, e Teleologia_&#8221; affermano che i metodi di studio sia per gli organismi viventi, sia per le macchine, sono simili in quanto non sono state trovare delle caratteristiche qualitativamente diverse che caratterizzano un gruppo e non l&#8217;altro.

Possiamo dividere le cause dei mutamenti della natura in quelli provocati da:

&#8211; cause efficienti: è l&#8217;agente che determina operativamente il mutamento

&#8211; cause finali: è l&#8217;intenzione di qualche essere vivente a raggiungere un certo scopo

I cibernetici puntano a descrivere il comportamento intelligente usando solo le cause efficienti, in quanto le cause finali sono caratteristiche dei sistemi biologici.

Come esempio possiamo considerare il comportamento della falena che è stato descritto da uno studioso americano con sole cause efficienti.

### Comportamento, Scopo, e Teleologia

Il comportamento intelligente può essere diviso in due grosse classi: il comportamento rivolto ad uno scopo (finalizzato), e il comportamento non rivolto ad uno scopo (causale).

Noi ci interessiamo al comportamento rivolto ad uno scopo. Ma cos&#8217;è uno scopo? Abbiamo un **tentativo riduzionista**, <span style="text-decoration: underline;">che riduce lo scopo ad un oggetto, e il suo raggiungimento è uno spostamento spazio/temporale dell&#8217;oggetto stesso</span>.

Su questa visione di vedere uno scopo si inseriscono i critici obiettando il fatto che non sempre lo scopo è un oggetto.

Il comportamento rivolto ad uno scopo può essere diviso a sua volta in comportamento rivolto ad uno scopo con retroazione (o teleologico) o senza retroazione (non teleologico).

Il comportamento rivolto ad uno scopo senza retroazione raggruppa tutti quei casi in cui il movimento è talmente veloce in cui è impensabile che ci sia del tempo utile a modificare il movimento mentre lo si sta facendo. Ad esempio, il comportamento di una rana mentre colpisce una mosca per mangiarsela, è senza retroazione.

Ci interesseremo al comportamento rivolto ad uno scopo con retroazione, nel quale l&#8217;azione che si sta svolgendo è modificabile mentre la si sta facendo. Questo tipo di comportamento è più efficace del comportamento senza retroazione, specialmente quando lo scopo è un oggetto fermo.

Il comportamento rivolto ad uno scopo con retroazione può essere ulteriormente diviso in comportamento rivolto ad uno scopo con retroazione non predittivo o non estrapolativo (la falena che cammina verso la luce) e predittivo o estrapolativo (il gatto che balza per catturare un topo nella posizione in cui il topo dovrebbe stare dopo il balzo, quindi il gatto è capace di estrapolare la posizione del topo in un istante di tempo futuro).

### Intelligenza e Comportamento rivolto ad uno scopo

Nell&#8217;articolo &#8220;_Coportamento, Scopo, e Teleologia_&#8221; non sono state individuate le condizioni necessarie e sufficienti per affermare che un agente ha il comportamento intelligente per raggiungere uno scopo. Questo perché il tentativo riduzionista per la descrizione di cosa si intende per scopo ci vincola troppo.

  * Condizione Necessaria: Supponiamo ci sia un cavaliere alla ricerca del Santo Graal. Se il Santo Graal non esiste, come descriviamo lo scopo di questo cavaliere se imponiamo che lo scopo sia un oggetto?
  * Condizione Sufficiente: Supponiamo una persona si sveglia all&#8217;improvviso durante la notte, e spara un colpo di pistola allo specchio. Come descriviamo lo scopo di questo signore? Il suo intento non era sparare nello specchio, ma l&#8217;ha fatto per motivi che non conosciamo.

Quindi la definizione di Scopo come una relazione spazio/temporale relativa ad un oggetto è troppo restrittiva per descrivere il comportamento intelligente rivolto ad uno scopo.

### Il ruolo dei Modelli nella Scienza

La cibernetica lavora con i **modelli**. Obiettivo della scienza è ottenere la **comprensione** ed il **controllo** di una qualche parte dell&#8217;universo. Ad esempio la lancetta del barometro che si abbassa ha come causa  (comprensione) l&#8217;abbassamento della pressione; ed anche, la cura per una malattia (controllo) mediante antibiotici.

Ma nessuna parte dell&#8217;universo si lascia afferrare senza un minimo di astrazione. I **modelli** ci aiutano proprio a questo: un modello formale (o intellettuale) rappresenta con astrazione un **sistema studiato** (cioè la parte dell&#8217;universo che stiamo studiando).

Possiamo dividere i modelli in:

  * **Modello materiale**: rappresentazione del _sistema studiato_ ottenuto mediante un altro sistema, di solito più semplice, ma con proprietà simili al _sistema studiato_.
  * **Modello Formale**: rappresenta in termini logici il _sistema studiato_ in maniera semplice, con proprietà simili.

I modelli materiali sono utili quando:

&#8211; Vogliamo studiare un sistema di un campo inconsueto (sistema studiato), in un campo più familiare (modello meccanico)

&#8211; Il modello materiale permette di svolgere esperimenti in condizioni più favorevoli rispetto a quelle date dal sistema studiato. Ad esempio ci conviene sperimentare nuovi farmaci prima sui topi, e poi sugli umani. Ma su quale base diciamo che un topo è un modello materiale dell&#8217;umano? Lo diciamo secondo alcuni criteri di &#8220;somiglianza&#8221; rispetto al modello originale.

I modelli non sono utili quando:

&#8211; Se il modello formale non rispecchia bene il sistema studiato, anche il modello materiale sarà poco significativo.

&#8211; Se il modello materiale suggerisce esperimenti predittibili dal modello formale, allora esso è superfluo.

Possiamo dividere i problemi in quelli a scatola chiusa e quelli a scatola aperta.

Nei problemi a **scatola chiusa** conosciamo solo alcuni input e possiamo verificare gli output, ma non sappiamo cosa avviene dentro la scatola. _La legge di trasformazione è quella legge che mette in relazione l&#8217;input con l&#8217;output_. Per scoprire cosa c&#8217;è nella scatola possiamo provare ad aprirla ed individuare altri input e/o altri output in modo da svolgere studi più approfonditi. Man mano che apriamo tutte le scatole trovate durante lo studio, abbiamo un problema a **scatola aperta**.

Nell&#8217;aprire le scatole, e quindi nell&#8217;aggiungere dettagli alla nostra descrizione, facciamo un&#8217;ipotesi di modularità, ipotizzando che gli input individuati siano debolmente accoppiati con gli altri elementi della scatola. Bisogna stare attenti quando si studiano questi problemi a scendere nel dettaglio fino ad un livello per noi soddisfacente, in modo da avere una buona descrizione del problema senza complicarlo in modo eccessivo.

## &#8220;Computer Simulation of Human Thinking&#8221; &#8211; Newell & Simon

Abbiamo discusso gli sviluppi della prima Cibernetica. Adesso ci spostiamo sul ramo della prima IA, ed esaminiamo il lavoro di Newell & Simon.

Newell & Simon, due neuroscienziati che studiavano la mente, avevano lo scopo di cercare dei **modelli del mentale**, ossia dei **modelli** che rappresentassero l&#8217;attività cognitiva umana.

Quindi volevano costruire dei programmi che simulassero i compiti cognitivi umani in modo psicologicamente realistico.

Per fare ciò si costruirono delle **Microteorie**. Ogni microteoria era relativa ad un particolare categoria di compiti cognitivi, ad esempio giocare a dama: essi chiedevano alla persona sotto esame di giocare a dama e pensare a voce alta, quindi riferire tutti i suoi ragionamenti selettivi ed euristici (introspezione).

Il programma risultante di questo studio, non solo doveva dare gli stessi risultati del ragionamento cognitivo (e quindi supera il test di Turing), ma nel calcolarli doveva elaborare le informazioni nello stesso modo di un essere umano. Quest&#8217;ultima condizione serve ad avere una simulazione psicologicamente realistica del ragionamento umano.

Una volta costruito un modello per un compito cognitivo, abbiamo una microteoria. Newell & Simon volevano trarre un modello della mente combinando tra loro tutte le microteorie ottenute.

La differenza con Turing, è che Newell & Simon consideravano il test di Turing &#8220;debole&#8221; in quando non riguarda i processi del pensiero, ma prende in considerazione solo la prestazione finale.

### Critiche al lavoro di Newell & Simon

**Critica sull&#8217;uso del protocollo verbale**

Il protocollo verbale, con il quale i soggetti studiati illustravano il proprio processo di pensiero sono **incompleti** perché non tutti i processi della mente sono accessibili all&#8217;introspezione.

Inoltre questo metodo di studio del mentale è scorretto perché pensare e descrivere cosa si sta pensando sono due compiti concorrenti che possono interferire tra loro.

Si sta studiando il modo di pensare, o il modo in cui un essere umano descrive il proprio pensiero?

**Critica sul dominio di applicazione**

Le microteorie sono strettamente collegate al particolare problema. Quindi applicando il modello suggerito da una microteoria ad un problema simile a quello di partenza non si hanno buoni risultati.

**Critica sul campione di persone**

Il campione scelto per eseguire i test è ristretto, e non rispecchia il modo di pensare di tutta la popolazione. Inoltre ogni persona ha un modo particolare di pensare.

**Critica sulla modularità**

Newell & Simon non fanno ipotesi di modularità sulla mente e la considerano interamente in un&#8217;unica architettura unificata. Successivi studi (Chomsky, Marr, Fodor, ed altri) tentano di dividere la mente in moduli, in modo da poterli studiare indipendentemente.

### Conclusioni

Il lavoro di Newell & Simon è stato fallimentare, ma il loro contributo all&#8217;IA è stato enorme. Tutt&#8217;oggi le euristiche da loro definite sono molto utilizzate.

## Chomsky ed il Linguaggio Universale

Un esempio di ipotesi di modularità è il **Linguaggio Universale** di Chomsky. Lui osserva come i bambini nei loro primi anni di vita riescono ad imparare la lingua, e nota che gli stimoli che essi ricevono sono di scarsa qualità per ottenere i risultati che si hanno.

Quindi l&#8217;ipotesi di modularità di Chomsky è che nella nostra mente esiste un modulo di **Grammatica Universale** (UG) che ci aiuta ad imparare il linguaggio parlato.

Quello che ha fatto Chomsky è isolare questo modulo UG dalle restanti parti della mente, e studiarlo a se stante.

Questo è proprio quello che manca nel lavoro fatto da Newell & Simon, in quanto non avendo fatto ipotesi di modularità, non riescono a trovare delle variabili in comune a tutti gli essere umani con le quali è possibile creare un modello di tutta la mente umana.

## David Marr

Marr, essendo allievo di Chomsky, prende da lui spunto, e nel suo articolo &#8220;Artificial Intelligence &#8211; A Personal View&#8221; espone la sua critica al lavoro di Newell & Simon.

Secondo Marr, un risultato nel campo dell&#8217;IA doveva seguire questi passaggi:

  1. Definizione di **cosa** è calcolato, e **perché** è calcolato
  2. Definire **come** calcolarlo, quindi definizione di un algoritmo
  3. Dimostrazione di funzionamento

Il &#8220;perché&#8221; non è interessante da definire in quanto è legato alla natura del problema: il mondo è fatto così. Il &#8220;cosa&#8221; invece è molto interessante, in quanto questo passaggio non è stato considerato da Newell & Simon. Infatti è difficile definire &#8220;cosa&#8221; calcolare in modo preciso quando si sta tentando di costruire un modello per l&#8217;intera mente umana.

Marri chiama _teorie di tipo 1_ quelle in cui si riesce a trovare una buona descrizione di cosa è calcolato, e chiama _teorie di tipo 2_ quelle in cui non si è ancora riusciti a dare una descrizione formale.

## Antonio Damasio

Molti hanno criticato Newell & Simon per mancanza di ipotesi di modularità. In realtà un&#8217;ipotesi di modularità è stata fatta: l&#8217;attività di problem solving della mente umana è considerata indipendente dalle emozioni provate.

Damasio, neurologo e neuroscienziato degli anni 80, nello studiare un caso clinico si accorge che il paziente non è in grado di provare emozioni.

Questo paziente è perfettamente in grado di effettuare ragionamenti razionali, e risponde correttamente a domande a lui poste. Però quando è coinvolto in prima persona non riesce a prendere le decisioni giuste con i suoi ragionamenti.

L&#8217;ipotesi di Damasio è che _le emozioni hanno un ruolo importante nel ragionamento pratico_.

Test effettuati con questo paziente mostrano che non è in grado di provare emozioni. Ad esempio in una partita a poker non prova tristezza se perde una mano di gioco, oppure riesce a parlare in modo freddo della sua malattia (o di eventi brutti) con freddezza.

Damasio va oltre questa ipotesi e ne formula un&#8217;altra, in cui afferma che, come le emozioni, _le immagini mentali hanno un ruolo nel ragionamento pratico_.

Supponiamo di essere stati morsi da un cane mentre passeggiavamo nel parco. Dopo qualche giorno se ripensiamo a quel cane, riusciamo ad immaginarlo e a ricostruirci nel nostro _buffer visivo_ la sua immagine. Assieme alla scena ricostruita associamo un&#8217;emozione che può essere bella o brutta a seconda se il morso del cane ci è piaciuto oppure no (ovviamente in questo caso non ci è piaciuto). Quindi in futuro cercheremo di non passare vicino a quel cane perché rischiamo di essere morsi nuovamente: così facendo nel nostro ragionamento pratico elimineremo tutti gli scenari possibili che ci portano nelle vicinanze di quel cane.

Damasio dice con questa ipotesi che il paziente da lui studiato è incapace associare le immagini mentali alle emozioni, e quindi nel suo ragionamento pratico può scegliere un&#8217;azione che lo riporta a commettere un errore già fatto in passato.

Con queste ipotesi Damasio ha cercato di spiegare l&#8217;assenza di pianificazione e di prudenza che ha il suo paziente durante i ragionamenti pratici che lo coinvolgono i prima persona.

Inoltre mostra come le emozioni hanno un ruolo centrale nel ragionamento, e quindi è sbagliato considerarle indipendenti dal problem solving. Quindi sarà possibile progettare macchine con prestazioni pari a quelle degli essere umani anche se non provano emozioni?
