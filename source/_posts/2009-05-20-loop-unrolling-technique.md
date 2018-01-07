---
title: Loop-Unrolling Technique
date: 2009-05-20T00:50:32+00:00
layout: post
comments: true
categories:
  - programming
tags:
  - algorithm
---
Lo &#8220;srotolamento&#8221; del ciclo consistente nel modificare il controllo del ciclo e nel replicare opportunamente le istruzioni all&#8217;interno del ciclo viene detto &#8220;tecnica di LOOP UNROLLING&#8221;.

<!--more-->

## VANTAGGI DEL LOOP UNROLLING

&#8211; Utilizzo ottimale dei processori con architettura pipelined

&#8211; Riduzione dell&#8217;overhead del ciclo di iterazione

&#8211; Riduzione del numero di trasferimenti fra i vari livelli memoria

&#8211; Aumento delle operazioni concorrenti

L&#8217;overhead del programma e il numero di trasferimenti di dati dai livelli più bassi di memoria ai registri Si riducono di un fattore proporzionale alla nuova lunghezza del ciclo (profondità dell&#8217;unrolling).

## SVANTAGGI DEL LOOP UNROLLING

&#8211; Aumento della memoria destinata al programma

&#8211; Perdita della generalità del codice*

* se si effettua l&#8217;unrolling a mano, mentre se si usa un compilatore per queste tecniche se ne risente di meno; ad esempio, il compilatore gcc supporta l&#8217;opzione &#8220;-unroll-all-loops&#8221; per effettuare automaticamente il loop unrolling.

## ESEMPIO DI APPLICAZIONE 1

I clicli:

for i=1 to n

a[i] = x(i) + i

endfor

for i=1 to n

b[i] = x(i) + i

endfor

Si possono unificare in:

for i=1 to n

a[i] = x(i) + i

b[i] = x(i) + i

endfor

## ESEMPIO DI APPLICAZIONE 2

Il ciclo:

for i=1 to n

if (i % 2) == 0

y(i)++;

else

y(i)&#8211;;

endfor

si puo&#8217; dividere in questo modo per evitare l&#8217;if:

for i=2 to n step 2

y(i)++;

endfor

for i=1 to n step 2

y(i)&#8211;;

endfor

## ESEMPIO DI APPLICAZIONE 2

Un ciclo del tipo:

for i=1 to n

y(i)=0

endfor

puo&#8217; essere modificato il passo del ciclo in questo modo:

for i=1 to n step 2

y(i)=0

y(i+1)=0

endfor
