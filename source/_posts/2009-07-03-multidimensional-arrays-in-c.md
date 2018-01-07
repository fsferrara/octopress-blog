---
title: Multidimensional Arrays in C
layout: post
comments: true
categories:
  - programming
tags:
  - array
  - c
  - pointers
---
Questo articolo tratta la gestione delle stringhe e, in generale, dei vettori multidimensionali nel linguaggio C.

## Allocazione di memoria del vettore

Sappiamo che nel linguaggio c dichiariamo un vettore con l&#8217;istruzione

int vett[n];

in questo modo creiamo un vettore chiamato vett di n elementi:

<!--more-->

vett[0] , vett[1] , &#8230; , vett[n-1]

Supponiamo, con n=5, di riempire il vettore in questo modo:

<table border="1">
  <tr>
    <td>
      10
    </td>

    <td>
      11
    </td>

    <td>
      12
    </td>

    <td>
      13
    </td>

    <td>
      14
    </td>
  </tr>
</table>

Risulterà che:

<pre lang="c">vett[0] = 10 = *vett
 vett[1] = 11 = *vett+1
 vett[2] = 12 = *vett+2
 vett[3] = 13 = *vett+3
 vett[4] = 14 = *vett+4</pre>

Inoltre supponiamo di aver fatto girare al computer il programma,

avremo alcuni indirizzi se stampiamo:

804400008 = vett

804400012 = vett+1

804400016 = vett+2

804400020 = vett+3

804400024 = vett+4

## Passare il vettore ad una funzione

Ora che sappiamo come viene creato un vettore in memoria affrontiamo

il problema di passare il vettore nelle funzioni. Supponiamo la funzione:

<pre lang="c">void funzione(int *vettore)
 {
 int i;

for (i=0 ; i&lt;n ; i++)
 vettore[i] += 20;
 }</pre>

che aggiunge 20 ad ogni elemento del vettore. Quale sarà la chiamata giusta

da fare nel programma chiamante?

<pre lang="c">main()
 {
 .
 .
 .
 funzione(vett);
 .
 .
 .
 }</pre>

Perchè passiamo &#8220;vett&#8221; e non &#8220;&vett&#8221;?

Il contenuto di &#8220;vett&#8221; non è altro che un indirizzo&#8230; il primo elemento del

vettore è &#8220;*vett&#8221; oppure &#8220;vett[0]&#8221;.

Quindi con questa chiamata non facciamo altro che passare per valore alla

funzione un indirizzo che è proprio l&#8217;indirizzo del nostro vettore :)

Praticamente nella funzione viene dichiarato un puntatore ad intero chiamato

&#8220;vettore&#8221;. La dichiarazione è

<pre lang="c">int *vettore</pre>

Quindi in vettore mettiamo l&#8217;indirizzo che nell&#8217;esempio è 804400008.

All&#8217;intrno della funzione risulterà che:

vettore   = 804400008          <&#8211; indirizzo

*vettore   = 10                 <&#8211; contenuto di vett[0]

*vettore+1 = 11                 <&#8211; contenuto di vett[1]

Questo è il motivo che nel linguaggio C non è obbligatorio definire la

dimensione del vettore!

## STAMPA SU VIDEO DI UN VETTORE v DI n ELEMENTI

<pre lang="c">void StampaVettore(int n, float *v)
 {
 int i;

printf("\n Vettore = ( ");
 for ( i=0 ; i&lt;n-1 ; i++ )
 printf("%.2f %s",v[i],", ");

printf("%.2f %s \n",v[n-1]," );");
 }</pre>

## STAMPA SU VIDEO DI UNA MATRICE M DI n RIGHE ED m COLONNE

<pre lang="c">void StampaMatrice(int n, int m, float **M)
 {
 int i,j;

for (i=0;i&lt;n;i++)
 {
 printf("\n");
 for (j=0;j&lt;m;j++) printf("%.2f %s",M[i][j],"   ");
 }
 printf("\n");
 }</pre>
