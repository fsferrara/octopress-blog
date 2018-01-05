---
comments: true
title: Disable Goku Script spam feature
date: 2009-07-28T17:39:01+00:00
author: fsferrara
layout: post
guid: http://www.fsferrara.com/?p=81
permalink: /disable-goku-script-spam-feature/
categories:
  - Internet
tags:
  - chat
  - irc
---
Eliminare lo spam dal goku script

Il goku script è uno script per mIRC realizzato nell’anno 2001 e tutt’oggi è considerato uno degli script più completi in circolazione. Lo script è [scaricabile a questo link](/portfolio/goku-script/).

Purtroppo nella sua distribuzione sono stati lasciati attivi i messaggi di spam (messaggi usati per pubblicizzare lo script stesso).

Di questi messaggi ne sono inviati due ogni volta che si entra o esce da un canale di chat&#8230; quindi se entriamo in un canale inviamo un messaggio di spam alla prossima persona che entra in uno dei canali in cui ci troviamo. Qui il codice dello script per mIRC:

<!--more-->

<pre lang="shell">on 1:JOIN:#:{
 if ($nick == $me) {
   ...
 }
 else {
   if (%joinkiff == on) { notice $nick $spam.line %script | set %joinkiff off }
 }
 :fine
}

on 1:PART:#:{
 if (%partkiff == on) { notice $nick $spam.line %script | set %partkiff off }
 }
}</pre>

Per disattivarli possiamo intervenire in questo modo&#8230;

## Disattivare messaggi spam

Dobbiamo eliminare il meccanismo che setta ad **on** le variabili _%joinkiff_ e _%partkiff_. Questo si trova nel file_

&#8220;.\system\remote\rgoku23.ini&#8221;_ (path relativo alla cartella in cui è installato lo script&#8230; di solito _C:\Programmi\Goku4\_)

alle righe 208 e 209 troviamo:

<pre>n206=  set %joinkiff on
n207=  set %partkiff on</pre>

modifichiamo queste due righe in:

<pre>n206=  set %joinkiff off
n207=  set %partkiff off</pre>

Questo è tutto&#8230; adesso il nostro goku script non spamma più :)

## Mirc Editor

La stessa modifica può essere effettuata usando il mIRC Editor, premendo **Alt+R** mentre mIRC è aperto. Basta selezionare il file rgoku23.ini (dal menu View) e cercare le righe da modificare.

La ricerca può essere fatta usando il Find Text (si trova sotto il menu Edit).

Buona Chat!!!
