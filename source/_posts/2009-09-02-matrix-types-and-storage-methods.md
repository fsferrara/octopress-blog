---
comments: true
title: Matrix types and Storage methods
date: 2009-09-02T01:01:43+00:00
author: fsferrara
layout: post
guid: http://www.fsferrara.com/?p=109
permalink: /matrix-types-and-storage-methods/
categories:
  - Programming
tags:
  - array
  - data structures
---
In mathematics, a matrix (plural matrices) is a rectangular array of numbers, symbols, or expressions, arranged in rows and columns. The individual items in a matrix are called its elements or entries.

In computer science the term &#8220;matrix&#8221; refers to a multidimensional array, that is a systematic arrangement of objects, usually in rows and columns.

In questo articolo si illustra i vari tidi di matrice, e i vari tipi di memorizzazione di matrice. Dal modo in cui sono collocati gli elementi all&#8217;interno di una matrice, possiamo distinguere vari tipi

<!--more-->

## Matrice SINGOLARE

e&#8217; una matrice triangolare (sueriore o inferiore), dove almeno un elemento a[i,i] della diagonale e&#8217; uguale a 0.

La caratteristica di una matrice triangolare e&#8217; che se fa parte di un sistema lineare, allora il sistema ammette infinite soluzioni.

Il determinante di una matrice singolare e&#8217; uguale a zero.

## Matrice A DIAGONALE DOMINANTE

matrice quadrate appartenente a R[nxn] di dice a diagonale dominante se per ogni i=1,2,&#8230;,n vale:

n

abs(a[i,i]) >=  sum  abs(a[i,j]) quando i != j

i,j=1

se vale il segno > allora di dice DIAGONALE STRETTAMENTE DOMINANTE

## Matrice DEFINITA POSITIVA

una matrice quadrata A appartenente a R[nxn], che e&#8217; simmetrice, si dice definita positiva se per qualsiasi vettore x appartenente a R[n], e x != 0, risulta:  x(trasposto) \* A \* x > 0

## Matrice ORTOGONALE

una matrice Q e&#8217; ortogonale se la sua inversa e&#8217; proprio uguale alla sua trasposta.

Da Q \* Q(inversa) = I  segue che Q \* Q(trasosta) = I

## Matrice CIRCOLANTE

e&#8217; una matrice dove il vettore riga k-esimo e&#8217; ottenuto dal vettore riga (k-1)-esimo shiftato circolarmente di una posizione verso destra:

Esempio:

1 2 3 4 5

5 1 2 3 4

4 5 1 2 3

3 4 5 1 2

2 3 4 5 1

## Matrici di TOEPLITZ

Sono uguali alle Matrici CIRCOLANTI, con la caratteristica che non viene effettuato lo shift circolare, ma ad ogni shift puo&#8217; etrare un nuovo elemento. Esempio

1 2 3 4 5

9 1 2 3 4

6 9 1 2 3

0 6 9 1 2

1 0 6 9 1

Una matrice di TOEPLITZ puo&#8217; essere immersa in una matrice CIRCOLANTE piu&#8217; grande in modo da poter usare algoritmi per matrici CIRCOLANTI.

## Matrice SIMMETRICA

Una matrice si dice simmetrica quando A\[i\]\[j\] = A\[j\]\[i\]

## Matrice BIDIAGONALE (superiore o inferiore)

Bidiagonale inferiore se: a(i,j)=0 per j>i e per i>j+1

Bidiagonale superiore se: a(i,j)=0 per i>j e per j>i+1

## Matrice TRIDIAGONALE

Matrice tridiagonale: se a(i,j)=0 per |i-j|>1

In una matrice tridiagonale di dim nxn gli elementi che bisogna effettivamente conservare sono quelli delle tre diagonali cioË sono 3n-2.

## Matrice SPARSA

E&#8217; una matrice a[n,m] in cui ci sono molti elementi uguali a 0. La sparsita&#8217; di una matrice si misura grazie al &#8220;Grado di sparsita'&#8221;:

numero coefficienti nulli

SP = &#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-

numero totale coefficienti

Quando gli elementi nulli sono 0, allora  -> SP = 0 |

|-> Quindi 0 <= SP <= 1

Quando non ci sono elementi nulli, allora -> SP = 1 |

La matrice e&#8217; molto sparsa quando SP e&#8217; molto vicino a 1.

## Matrice A BANDA

Ampiezza di banda inferiore=p, ampiezza di banda superiore=q  se a(i,j)=0 per i>j+p e per j>i+q

## CONFRONTO: SIMMETRICA DIAGONALE DOMINANTE E SIMMETRICA DEFINITA POSITIVA

|-Simmetrica                        |-Simmetrica

se   A = |                         =>    A = |                         ?

|-Diagonale dominante               |-Definita positiva

Ovvero quando una matrice simmetrica a diagonale dominante e&#8217; anche definita positiva? L&#8217;affermazione e&#8217; vera quando A e&#8217;:

&#8211; non singolare (det(A)>0)

&#8211; simmetrica

&#8211; a diagonale dominante

&#8211; ha gli elementi sulla diag non negativi

# Tipi di Memorizzazione per una Matrice

A secondo del tipo di matrice, possiamo scegliere il metodo di memorizzazione più adatto alle nostre esigenze. Le memorizzazioni sono spesse scelte per ottimizzare lo spazio su disco e i calcoli sulle matrici, come:

1) Prodotto scalare tra due vettori

Da come risultato uno scalare.

2) Prodotto Matrice-Matrice

Basato sul prodotto scalare di sue vettori.

A[nxm] * B[mxp] = C[nxp]

3) Norma 1 di una matrice

Data una matrice facciamo la somma degli elementi riga per riga. La norma 1 sara&#8217; uguale al massimo, in valore assoluto, di tutte le somme ottenute.

4) Norma infinito di una matrice

Data una matrice facciamo la somma degli elementi colonna per colonna. La norma 1 sara&#8217; uguale al massimo, in valore assoluto, di tutte le somme ottenute.

Qui vi sono alcuni metodi di memorizzazione:

## BAND STORAGE

Questa memorizzazione e&#8217; utile per memorizzare matrici a banda. Si consideri la seguente matrice a bandauna matrice 6&#215;6 con p=1 e q=2

a(1,1) a(1,2) a(1,3)

a(2,1) a(2,2) a(2,3) a(2,4)

a(3,2) a(3,3) a(3,4) a(3,5)

a(4,3) a(4,4) a(4,5) a(4,6)

a(5,4) a(5,5) a(5,6)

a(6,5) a(6,6)

questa matrice viene memorizzata nel formato BAND STORAGE nel seguente modo:

\*      \*   a(1,3) a(2,4) a(3,5) a(4,6)

*   a(1,2) a(2,3) a(3,4) a(4,5) a(5,6)

a(1,1) a(2,2) a(3,3) a(4,4) a(5,5) a(6,6)

a(2,1) a(3,2) a(4,3) a(5,4) a(6,5)    *

## PACKED STORAGE

Questa memorizzazione e&#8217; utile per matrici simmetriche oppure triangolari (inferiori o superiori). Si consideri la seguente matrice triangolare:

a(1,1) a(1,2) a(1,3) a(1,4) a(1,5)

a(2,2) a(2,3) a(2,4) a(2,5)

a(3,3) a(3,4) a(3,5)

a(4,4) a(4,5)

a(5,5)

questa matrice memorizzata in PACKED STORAGE per righe:

a(1,1) a(1,2) a(1,3) a(1,4) a(1,5) a(2,2) a(2,3) a(2,4) a(2,5) a(3,3) a(3,4) a(3,5) a(4,4) a(4,5) a(5,5)

mentre memorizzata in PACKED STORAGE per colonne:

a(1,1) a(1,2) a(2,2) a(1,3) a(2,3) a(3,3) a(1,4) a(2,4) a(3,4) a(4,4) a(1,5) a(2,5) a(3,5) a(4,5) a(5,5)

## MEMORIZZAZIONE CON TRE VETTORI

Questa memorizzazione e&#8217; utile per matrici sparse.

Dicendo &#8220;nz&#8221; il numero di elementi non nulli dela matrice sparsa A ed n la sua dimensione, si memorizza la matrice in tre vettori:

R[nz]  = (elementi non nulli riga per riga)

J[nz]  = (indici di colonna degli elementi di R[])

I[n+1] = (posizione in R del primo elemento non nullo di ogni riga di A; L&#8217;ultimo elemento e&#8217; I(n+1)=nz+1)
