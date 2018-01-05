---
comments: true
title: ISDN Technology
date: 2010-01-09T01:28:47+00:00
author: fsferrara
layout: post
guid: http://www.fsferrara.com/?p=124
permalink: /isdn-technology/
categories:
  - System Administration
tags:
  - Asterisk
  - ISDN
  - PBX
---
Integrated Services Digital Network, o ISDN, è una rete digitale che dà supporto a molti servizi di voce e dati. La definizione tecnica dell&#8217;ISDN, che investe diverse componenti delle reti, risale alle raccomandazioni ITU-T della serie I del 1984 e comprende numerose altre pubblicazioni dello stesso ITU-T e dell&#8217;ETSI (European Telecommunications Standard Institute) fatte negli anni successivi.

<!--more-->

## **Integrated Services Digital Network &#8211; ISDN

**

ISDN è un servizio di _telefonia digitale_ basato sul protocollo ISDN. Quindi con il termine ISDN ci riferiamo sia al protocollo, sia al servizio implementato dal protocollo stesso.

ISDN: protocollo che descrive come si svolgono le chiamate

Una rete ISDN è quindi una rete digitale anche integrata nei servizi, in cui le diverse parti, il terminale, la rete di accesso, la rete di trasporto, sono realizzate per offrire gli stessi servizi. Elementi fondamentali per il supporto di tali servizi sono il protocollo di segnalazione della rete di trasporto ISUP (ITU-T Q.767) e della rete di accesso DSS1 (ITU-T Q.931), che fanno parte della pila di protocolli del sistema di segnalazione a canale comune n°7 insieme ad altri descritti nelle Racc. ITU-T serie Q. Attraverso tali protocolli vengono trasportate le informazioni che consentono l&#8217;espletamento dei diversi servizi; un esempio per tutti l&#8217;identità del chiamante, che viene trasportata dai protocolli di segnalazione dalla rete del chiamante verso la rete e il terminale del chiamato.

In Europa è usata la variante ISDN-DSS1 sviluppata da ETSI (European Telecomunications Standards Institute).

Sull&#8217;accesso BRA ISDN sono disponibili una serie di nuovi servizi come la segnalazione del numero telefonico di chi chiama (Caller ID) e il multinumero, cioè la possibilità di avere fino ad otto numeri telefonici sullo stesso abbonamento, ciascuno assegnato ad un apparecchio diverso (es. uno per il telefono, uno per il fax, uno per il modem in ingresso&#8230;). La tecnologia digitale utilizzata da ISDN garantisce una qualità audio molto elevata, eliminando completamente la diafonia e buona parte dei disturbi presenti nella tradizionale telefonia . In Italia ISDN BRA viene fornito in modalità mononumero o multinumero: è possibile cioè richiedere fino a 7 numeri telefonici diversi oltre al numero principale. Sempre sull&#8217;accesso base (BRA), che comprende 2 canali B a 64 Kbit/sec, è possibile collegarsi ad Internet sia ad una velocità di 64 Kbit/s, pagando una semplice telefonata, sia, se il Provider utilizzato lo permette, ad una velocità di 128 Kbit/s, sostenendo però il costo di due chiamate contemporanee. Inoltre sono disponibili i servizi di avviso di chiamata, conferenza a tre, presentazione dell&#8217;identità del chiamante (Caller ID), trasferimento di chiamata e per alcuni Operatori anche il servizio di richiamata su occupato.

Molto diffusa in Italia un tipo particolare di NT, chiamata NT1+, che ha al suo interno anche un Terminal Adapter (TA) a/b, capace di gestire due porte analogiche, permettendo cosi&#8217; di connettere direttamente all&#8217;NT1+ apparati analogici come telefoni tradizionali o fax di gruppo 3. L&#8217;installazione della borchia ISDN deve essere richiesta al proprietario della rete.

Una ulteriore configurazione degli accessi è il &#8220;punto-punto&#8221; e &#8220;punto-multipunto&#8221; che in buona sostanza esprime il modo di dialogare della rete con uno o più terminali lato utente. La configurazione &#8220;punto-punto&#8221; è adottata in presenza, lato utente, di centralini (PABX)collegati sia su accesso primario che in pool di accessi base. La configurazione punto-multipunto è adottata ad esempio negli accessi base in cui sul bus isdn sono collegati dispositivi con numeri diversi (MSN) quali telefoni isdn, modem isdn, fax G4. La differenza tecnica che contraddistingue anche le due tipologie è il cosiddetto TEI, che viene utilizzato nel protocollo ISDN, per il quale una punto-punto è fisso a zero, mentre sulla punto-multipunto è variabile e deciso dalla centrale pubblica. Per capire se la tipologia e punto-punto o punto-multipunto, soprattutto nel caso di accesso base mononumero, bisogna contattare l&#8217;operatore che fornisce il servizio, non esistono veri e propri standard.

**<span style="text-decoration: underline;">CALLER-ID</span>:** è la funzione che ci permette di vedere il numero di chi ci chiama.

**<span style="text-decoration: underline;">MULTINUMERO</span>:** Possibilità di avere fino a 8 numeri su una singola linea ISDN. Ovviamente bisognerà assegnare un numero per ogni apparecchio.

Il collegamento ISDN più diffuso è quello base, a due canali (detto BRI):

  * 1° Canale: 64 kbit/s
  * 2° Canale: 64 kbit/s
  * 3° Canale aggiuntivo: 16 kbit/s (usato per le segnalazioni)

La banda totale e&#8217; 144 kbit/s!!! Di questa banda, solo i canali da 64 kbit/s sono sfruttati per trasferire informazioni utili all&#8217;utente finale, quindi in effetti l&#8217;utente beneficia di 128 kbit/s (sempre teorici)

## Architettura ISDN

### Alcuni termini

  * **NT (Network Terminator)**: Traduce il segnale proveniente dalla centrale telefonica, mediante _U-BUS_, in segnale utilizzabile dai nostri dispositivi ISDN, su _S-BUS_. Inoltre il Network Terminator permette di attaccarci
  * **TA (Terminal Adapter)** : Permette di allacciare vecchi dispositivi analogigi al Network Terminator, in moda da poterli riutilizzare. E&#8217; indicato per i vecchi FAX ;-) .

### Esempio NT (Network Terminator)

Un Network Terminator, che prende in ingresso un U-Bus dalla linea ISDN, e caccia in output due S-Bus per allacciarci due dispositivi ISDN (ad esempio due telefono ISDN).

Notiamo che in S-Bus non è che un cavo ethernet, usato per ISDN&#8230; e (forse) per U-Bus si usa il doppino telefonico, o anche in questo caso un cavo ethernet.

## Configurazione di ISDN

Una linea ISDN può avere varie configurazioni, in modo da adattarsi all&#8217;hardware con il quale deve funzionare (esempio PBX &#8211; centralino telefonico).

### Canali

ISDN supporta due tipi di canali:

**-> Canale B** (Bearer): sono canali utilizzati per i dati ed hanno una banda prefissata di 64 kbit/s.

**-> Canale D** (Delta): sono canali usati per segnalazioni e controllo; in particolari configurazioni possono essere usati anche per i dati. La banda passante assegnata ad un canale D varia al variare del tipo di _Accesso ISDN_.

### Accesso ISDN

Esistono due tipi di accesso ISDN:

  * **Accesso BRI [Basic Rate Interface &#8211; Accesso Base]**:&#8211; 2 canali B&#8211; 1 canale D a 16 kbit/s==> Totale 2B+D = 144 kbit/s
  * **Accesso PRI T1 [Basic Rate Interface &#8211; Accesso Base]**: (America, Giappone)&#8211; 23 canali B&#8211; 1 canale D a 64 kbit/s==> Totale 23B+D = 1536 kbit/s
  * **Accesso BRI E1 [Basic Rate Interface &#8211; Accesso Base]**: (Europa, Asia, Australia)&#8211; 30 canali B&#8211; 2 canale D a 64 kbit/s==> Totale 30B+2D = 2048 kbit/s

### Funzionamento Chiamate

I canali D sono usati per _iniziare_ le chiamate. Una volta che la chiamata è iniziata, ad essa è allocato un canale B&#8230; quindi per ogni chiamata deve essere disponibile un canale B (sempre di 64 kbit/s).

Notiamo come i canali B sono allocati sempre in modo dinamico!

## Considerazioni Tecniche

L&#8217;evoluzione di ISDN l&#8217;ha portato ad essere adottato in anbito aziendale. Queste ultime scelgono spesso tra due opzioni di installazione: il _multinumero_ e la _selezione passante_.

### Multinumero

E&#8217; un servizio opzionale.  <span class="blue-pen">Permette di avere un massimo di 8 terminali, sullo steso S-BUS, ognuno raggiungibile direttamente dall&#8217;esterno con un suo proprio numero telefonico</span>.

  * Possibile solo su ISDN accesso base (BRI)
  * Solo due terminali possono essere attivi contemporaneamente
  * Non chiede l&#8217;installazione di un PBX
  * Le chiamate interne sono a pagamento
  * NT (Network Terminator) deve essere configurato punto-multipunto

### Selezione Passante

E&#8217; un servizio opzionale.  <span class="blue-pen">Permette di raggiungere direttamente i terminali interni appoggiandoci su un PBX (centralino telefonico). Non si ha il limite di 8 terminali su ogni linea ISDN</span>.

  * Possibile sia su linee BRI, sia su linee PRI
  * Non c&#8217;è limite al numero di terminali interni attivi contemporaneamente
  * Chiede l&#8217;instllazione di un PBX
  * Le chiamate interne NON sono a pagamento
  * NT (Network Terminator) deve essere configurato punto-punto

### Considerazioni

Il multinumero si adatta solo in pochi casi&#8230; spesso perche&#8217; sono richieste telefonate interne gratuite!

<span class="blue-pen"><br /> Ad esempio possiamo avere cinque ingressi ISDN: ipotizziamo i numeri telefonici da 02160291<span style="text-decoration: underline;">01</span> a 02160291<span style="text-decoration: underline;">05</span> (Le ultime due cifre individuano la linea fisica, e sono 5 BRI &#8211; quindi max 10 telefonate esterne contemporaneamente).<br /> Grazie alla selezione passante riusciamo ad avere i numeri da 02160291<span style="text-decoration: underline;">00</span> a 02160291<span style="text-decoration: underline;">99</span>&#8230; un range di ben 100 numero!<br /> </span>
