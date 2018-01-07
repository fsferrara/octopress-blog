---
title: Very brief introduction to Regular Expressions
layout: post
comments: true
categories:
  - programming
  - system administration
tags:
  - regex
  - regular-expression
---
Le espressioni regolari sono utili per descrivere la validità di valori, come ad esempio valori di attributi, dati caratteri, e qualsiasi tipo di valore esprimibile con un certo alfabeto.

Il concetto di espressione regolare è un formalismo importante utilizzato, in varie forme, in svariate applicazioni&#8230; ad esempio nei linguaggi di schema (come DTD di XML) per descrivere sequenze di elementi o caratteri. I linguaggi regolari sono utilizzati in molte altre aree dell&#8217;informatica oltre a XML, dall&#8217;elaborazione del testo e del linguaggio naturale alla verifica formale dei componenti hardware.

Potrebbe essere necessario, ad esempio, vincolare un valore &#8216;data&#8217; in modo tale da rispettare il formato dd-mm-yyyy, ovvero sia composto da due cifre per il giorno, seguite da due per il mese e quattro per l&#8217;anno, tutto separato da un segno meno “-”. Alternativamente possiamo specificare che un certo valore deve essere un numero intero.

Chiamiamo Σ un alfabeto consistente in un insieme di atomi, che tipicamente sono caratteri Unicode o nomi di elementi. Un&#8217;espressione regolare su Σ è costruita in base alle seguenti regole:

<!--more-->

  * ogni atomo in Σ, preso da solo, è un espressione regolare;
  * se a e b sono espressioni regolari, allora lo sono anche le seguenti:
      * <pre>a?</pre>

      * <pre>a*</pre>

      * <pre>a+</pre>

      * <pre>a b</pre>

      * <pre>a|b</pre>

      * <pre>(a)</pre>

Gli operatori ?, , e + hanno una precedenza superiore alla concatenazione (l&#8217;operatore vuoto o “giustapposizione”), che a sua volta ha una precedenza superiore a |. E&#8217; sempre possibile usare le parentesi per raggruppare sotto-espressioni, superando così le precedenze di default. L&#8217;espressione ab\*|c, in cui l&#8217;alfabeto Σ contiene a, b, e c, è interpretata come (a(b\*))|c e non a(b*|c).

Una stringa finita di atomi di Σ può corrispondere o meno a una data espressione regolare a:

  * un atomo r appartenente a Σ corrisponde unicamente al singolo atomo r;
  * a? corrisponde ad a opzionalmente, ovvero a qualsiasi stringa corrisponda ad a più la stringa vuota;
  * a* corrisponde a zero o più ripetizioni delle stringhe che corrispondono ad a;
  * a+ corrisponde ad una o più ripetizioni delle stringhe che corrispondono ad a;
  * a b corrisponde a ciò a cui corrisponde &#8216;a&#8217; seguito da ciò a cui corrisponde b;
  * a|b corrisponde all&#8217;unione delle corrispondenze di a e b;
  * (a) ha le stesse corrispondente di a.

L&#8217;espressione regolare (a(b*))|c corrisponde così a tutte le stringhe composte da una a seguite da zero o più b, oppure una singola c da sola.

Un linguaggio regolare è un insieme di stringhe che corrispondono a una qualche espressione regolare.

E&#8217; possibile definire un&#8217;espressione regolare d (che sta per digit, cifra) scrivendo:

<pre>0|1|2|3|4|5|6|7|8|9</pre>

laddove l&#8217;alfabeto è composto ad esempio da tutti caratteri Unicode. Possiamo partire da questa definizione per definire un&#8217;altra espressione regolare &#8216;data&#8217; scrivendo dd-dd-dddd. Naturalmente quest&#8217;espressione corrisponde anche a stringhe come 88-26-9995, che non denotano date reali, ma con un po&#8217; più di sforzo è possibile catturare precisamente l&#8217;insieme di stringhe desiderato: in effetti su può usare un linguaggio regolare per gestire correttamente anche gli anni bisestili, ma allora le cose si fanno parecchie complicate!

La seguente espressione regolare descrive gli interi con un alfabeto composto dalle dieci cifre e dal segno meno:

<pre>0|-?(|1|2|3|4|5|6|7|8|9)(0|1|2|3|4|5|6|7|8|9)*</pre>

Secondo questa definizione, -42, 0, 117 sono accettabili, mentre 000, -0 e 3.14 non lo sono.

Adesso facciamo l&#8217;ultimo esempio, più complicato! In XHTML il contenuto di un elemento table dev&#8217;essere una sequenza che consiste in un elemento opzionale &#8216;caption&#8217; seguito da un certo numero di elementi &#8216;col&#8217; o alternativamente &#8216;colgroup&#8217;, i quali a loro volta sono opzionalmente seguiti da un elemento &#8216;thead&#8217; e uno &#8216;tfoot&#8217;, per concludere almeno un elemento &#8216;tbody&#8217; (o alternativamente &#8216;tr&#8217;). Possiamo scrivere con un&#8217;espressione regolare:

<pre>caption? ( col* | colgroup* ) thead? tfoot? ( tbody+ | tr+ )</pre>

Esistono molte varianti delle espressioni regolari&#8230; ad esempio le regular expression del linguaggio perl: tuttavia la maggior parte di queste varianti si limita ad aggiungere zucchero sintattico alla notazione base che abbiamo appena presentato.

Un&#8217;estensione tipica sono gli intervalli di caratteri: [0-9], ad esempio, è una comoda abbreviazione per indicare le cifre al posto di 0|1|2|3|4|5|6|7|8|9. In modo analogo a{n,m} con n e m numeri interi non negativi, denota da n ad m ripetizioni di a.

Questa è l&#8217;introduzione alle espressioni regolari; per lavorare efficientemente con un vero implementazione di queste espressioni richiede ulteriore studio.
