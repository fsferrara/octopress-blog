---
comments: true
title: The Web and the problem of Privacy
date: 2009-06-27T20:53:03+00:00
author: fsferrara
layout: post
guid: http://www.fsferrara.com/?p=58
permalink: /web-and-privacy/
categories:
  - Security and Privacy
tags:
  - p3p
  - privacy
---
## Introduzione alla problema della privacy

Tempo fa il problema della privacy non era sentito perché dovevamo fidarci solo di un insieme ristretto di persone; con Internet, e le moderne tecnologie, è diventato facilissimo raccogliere, scambiare, e trasferire informazione.

C&#8217;è perdita di controllo su _cosa è raccolto_ e soprattutto _come è utilizzato_.

Il problema della privacy può sembrare una sciocchezza, ma un esempio vi farà cambiare subito idea!

Quando un paziente è sfortunatamente ricoverato in ospedale i suoi dati sono a disposizione di: medico curante, medico specialistico, ospedale, infermieri, e farmacia&#8230; tutte persone con le quali il paziente deve condividere i suoi dati.

Cosa succede se uno di questi ruba i dati dei pazienti e li rivende illegalmente ad enti che ne faranno uso improprio???

**Si racconta (ed è una storia vera) che un funzionario di banca, in servizio in un comitato statale relativo alla sanità, ebbe accesso alla lista dei pazienti diagnosticata di tumore. Collegò i dati alla lista dei suoi clienti e annullò i prestiti.** Adesso vi è chiaro il problema della privatezza?

<!--more-->Purtroppo i dati medici non sono gli unici dati ad essere sensibili; il Garante della Privacy in Italia nella Legge 675/96 che regola la raccolta, mantenimento, e divulgazione di informazioni personali, impone di chiedere sempre il consenso prima di raccogliere dati e definisce Dato Sensibile nell&#8217;articolo 22, comma 1: &#8220;

_I dati personali idonei a rivelare l&#8217;origine razziale ed etnica, le convinzioni religiose, filosofiche o di altro genere, le opinioni politiche, l&#8217;adesione a partiti, sindacati, associazioni od organizzazioni a carattere religioso, filosofico, politico o sindacale, nonché i dati personali idonei a rivelare lo stato di salute e la vita sessuale, possono essere oggetto di trattamento solo con il consenso scritto dell&#8217;interessato e previa autorizzazione del Garante._&#8221;

## Anonimizzatori (Anonymous Surfers)

I dati sono sempre raccolti sul Web mentre navighiamo, sfruttando varie tecniche come Link referenziali, File di log, Cookies, ecc&#8230; non sto qui a raccontarvi i dettagli tecnici di queste tecniche (ma se siete interessati contattatemi pure ;-) ), ma vi presento subito un modo per evitare di lasciare traccie in giro: gli Anonymous Surfers!

Un Anonymous Surfer, o anonimizzatore, maschera il tuo indirizzo IP: infatti mentre navighi in Internet il tuo indirizzo ip e visibile a ogni server, e puoi essere rintracciato da chiunque. Navigando con un anonimizzatore invece non sarà il tuo indirizzo ip ad essere visibile, ma sarà visibile l&#8217;indirizzo dell&#8217;anonimizzatore stesso. A questo punto dobbiamo solo sperare che l&#8217;Anonymous Surfer non imbrogli e raccolga dati illegalmente!

Esempi di Anonymous Surfer sono http://anonymouse.org/ , http://proxify.co.uk/ , http://www.shadowsurf.com/ , e cercando su Google se ne trovano molti altri. Per usarli basta collegarci al sito e seguire le semplici istruzioni&#8230; spesso basta digitare l&#8217;indirizzo del Sito Web che vogliamo visitare.

### 1+1=2

Dopo questa semplice introduzione&#8230; sapete cosa deve fare uno sfortunato malato di epatite o tumore per cercare in rete informazioni sulla sua malattia? DEVE USARE UN COMPUTER PUBBLICO O ALMENO UTILIZZARE UN ANONIMIZZATORE!!!

Per assurdo un motore di ricerca (gestito in modo illegale) potrebbe incrociare i suoi log sul server con i dati di un ISP (Internet Service Provider, suo complice) per sostituire l&#8217;indirizzo IP nei log con l&#8217;intestatario della linea telefonica, in modo da sapere chi ha cercato cosa :-)

## Raccolta di Dati su Web

Purtroppo le persone sono ancora poco sensibili al problema della privacy, e rilasciano facilmente i propri dati sul Web utilizzando Social Network, o partecipando a questionari e sondaggi&#8230; quante volte hai trovato un &#8220;Religione: Ateo&#8221; oppure &#8220;Fumo: 3 pacchetti al giorno&#8221; su un social network???

La FTC (Federal Trade Commission) è un ente che ha identificato cinque punti principali che un sito web dovrebbe rispettare per garantire privacy dei suoi utenti (Notifica, Consenso, Accesso, Sicurezza, Implementazione&#8230; manca però la richiesta di Cancellazione dei dati). Oltre alla FTC sono nati i **Seal Program**; enti che garantiscono la protezione della privacy da parte di alcuni siti web&#8230; quindi quando su un sito troviamo il sigillo di TRUSTe (http://truste.org/), BBBOnLine, WebTrust, o altri, abbiamo una certa sicurezza che quel sito web non faccia uso improprio dei nostri dati personali.

## P3P &#8211; Platform for Privacy Preferences Project

P3P è un modo per specificare le nostre preferenze di privacy direttamente nel browser, in modo che il controllo sia fatto in automatico con i vari siti web in cui navighiamo. P3P lo ritroviamo in tutti i moderni browser, ad esempio in Internet Explorer. Altri browser come Firefox, Opera, Safari, ed altri supportano in modo equivalente P3P. Purtroppo queste interfacce grafiche non ci permettono molto dettaglio nella configurazione&#8230; avendo a disposizione un plugin avanzato per P3P, un utente può configurare il browser in modo da essere avvisato quando un sito che richiede i dati anagrafici dichiara che li utilizzerà anche per inviare materiale commerciale.

### Applicare P3P al proprio Sito Web

Un web master può applicare P3P al proprio sito web in quattro semplici passi:

1) Creare il file /w3c/p3p.xml in questo modo:

<pre lang="XML">&lt;META xmlns="http://www.w3.org/2002/01/P3Pv1"&gt;
 &lt;POLICY-REFERENCES&gt;
 &lt;POLICY-REF about="http://www.nomesito.it/w3c/p3p_full.xml#FireTeamPolicy"&gt;
 &lt;INCLUDE&gt;/*&lt;/INCLUDE&gt;
 &lt;COOKIE-INCLUDE name="*" value="*" domain="*" path="*"/&gt;
 &lt;/POLICY-REF&gt;
 &lt;/POLICY-REFERENCES&gt;
&lt;/META&gt;</pre>

2) Creare il file /w3c/p3p_full.xml in questo modo:

<pre lang="XML">&lt;POLICIES xmlns="http://www.w3.org/2002/01/P3Pv1"&gt; &lt;!-- Versione P3P --&gt;

&lt;POLICY name="FireTeamPolicy" discuri="http://www.nomesito.it/w3c/privacy.html" opturi="http://www.nomesito.it/w3c/privacy.html"&gt;
&lt;!-- discuri e opturi contengono una versione human readable della politica p3p --&gt;

 &lt;!-- Prevengo inconvenienti durante lo sviluppo della politica P3P --&gt;
 &lt;TEST /&gt;

 &lt;!-- Nome del Sito e lista dei contatti --&gt;
 &lt;ENTITY&gt;
 &lt;DATA-GROUP&gt;
 &lt;DATA ref="#business.name"&gt;nomesito.it&lt;/DATA&gt;
 &lt;DATA ref="#business.contact-info.postal.street"&gt;Garibaldi, 110&lt;/DATA&gt;
 &lt;DATA ref="#business.contact-info.postal.city"&gt;Avellino&lt;/DATA&gt;
 &lt;DATA ref="#business.contact-info.postal.stateprov"&gt;AV&lt;/DATA&gt;
 &lt;DATA ref="#business.contact-info.postal.postalcode"&gt;83100&lt;/DATA&gt;
 &lt;DATA ref="#business.contact-info.postal.country"&gt;Italy&lt;/DATA&gt;
 &lt;DATA ref="#business.contact-info.online.email"&gt;nome@nomesito.it&lt;/DATA&gt;
 &lt;DATA ref="#business.contact-info.online.uri"&gt;www.nomesito.it&lt;/DATA&gt;
 &lt;DATA ref="#business.contact-info.telecom.telephone.intcode"&gt;+39&lt;/DATA&gt;
 &lt;DATA ref="#business.contact-info.telecom.telephone.loccode"&gt;0825&lt;/DATA&gt;
 &lt;DATA ref="#business.contact-info.telecom.telephone.number"&gt;120031&lt;/DATA&gt;
 &lt;/DATA-GROUP&gt;
 &lt;/ENTITY&gt;

 &lt;ACCESS&gt;&lt;nonident/&gt;&lt;/ACCESS&gt;

 &lt;DISPUTES-GROUP&gt;
 &lt;DISPUTES resolution-type="independent"
 service="http://www.nomesito.it"
 short-description="nomesito.it"&gt;
 &lt;IMG src="http://www.nomesito.it/w3c/logo.png" alt="Privacy Logo"/&gt;
 &lt;REMEDIES&gt;&lt;correct/&gt;&lt;/REMEDIES&gt;
 &lt;/DISPUTES&gt;
 &lt;/DISPUTES-GROUP&gt;

 &lt;STATEMENT&gt;
 &lt;CONSEQUENCE&gt;Our hosting service keep standard web server log&lt;/CONSEQUENCE&gt;
 &lt;PURPOSE&gt;&lt;admin/&gt;&lt;current/&gt;&lt;develop/&gt;&lt;/PURPOSE&gt;
 &lt;RECIPIENT&gt;&lt;ours/&gt;&lt;/RECIPIENT&gt;
 &lt;RETENTION&gt;&lt;stated-purpose/&gt;&lt;/RETENTION&gt;
 &lt;DATA-GROUP&gt;
 &lt;DATA ref="#dynamic.clickstream"/&gt;
 &lt;DATA ref="#dynamic.http"/&gt;
 &lt;/DATA-GROUP&gt;
 &lt;/STATEMENT&gt;

&lt;/POLICY&gt;

&lt;/POLICIES&gt;</pre>

3) Nell&#8217;esempio non sono illustrati particolari usi delle informazioni raccolte, in questo passo si dovrebbero rivedere i file p3p.xml e p3p_full.xml in base alle proprie esigenze. Inoltre si deve avere un&#8217;immagine a piacere w3c/logo.png, e un file (w3c/privacy.html) in cui è scritta la politica di privatezza in linguaggio naturale (cioè in Italiano!!!).

4) Copiare i file sul server e testarli con il validatore all&#8217;indirizzo http://www.w3.org/P3P/validator.html

Purtroppo P3P è solo un modo per negoziare automaticamente politiche sulla privacy, ma non ci assicura che effettivamente quel sito web rispetti quello che dichiara&#8230; però se il server ha una politica P3P e non la rispetta, allora è attaccabile legalmente. E&#8217; bene fidarsi sempre in presenza di un sigillo da parte di un Seal Program :-)

## Conclusioni

Il giusto equilibrio si può trovare con il buon senso, ricordando che ogni nostra pubblicazione su internet è di dominio pubblico&#8230; ricordando però che ci sono cose di cui andiamo orgogliosi e che potremo diffondere.

E’ bene quindi dare poche informazioni su di noi, sia nelle pagine pubbliche disponibili sulla rete che a privati sconosciuti o conosciuti in rete. In particolare, gli esperti raccomandano ai minori di:

  * Evitare di condividere foto che mostrano il proprio aspetto
  * Non rivelare mai il proprio indirizzo fisico o numero di telefono
  * Non rivelare mai i propri dati anagrafici
  * Nascondere le proprie preferenze politiche, religiose, sessuali, o altro che potrebbe causarti problemi

La prima raccomandazione è in contrasto con la partecipazione a molte reti sociali&#8230; ma hai ancora voglia di scrivere sul tuo Social Network preferito?
