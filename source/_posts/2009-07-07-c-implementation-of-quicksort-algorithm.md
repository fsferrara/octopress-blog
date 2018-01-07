---
title: C implementation of Quicksort algorithm
layout: post
comments: true
categories:
  - programming
tags:
  - algorithm
  - c
  - sort
---
Quicksort è un ottimo algoritmo di ordinamento ricorsivo in place che, come merge sort, si basa sul paradigma divide et impera. La base del suo funzionamento è l&#8217;utilizzo ricorsivo della procedura partition: preso un elemento da una struttura dati (es. array) si pongono gli elementi minori a sinistra rispetto a questo e gli elementi maggiori a destra.

> Il Quicksort, termine che tradotto letteralmente in italiano indica ordinamento rapido, è l&#8217;algoritmo di ordinamento che ha, in generale, prestazioni migliori tra quelli basati su confronto; è stato sottoposto a un&#8217;analisi matematica approfondita ed estremamente precisa, tanto che le sue prestazioni sono state comprese a fondo e il suo comportamento è stato descritto in modo molto accurato.
>
> <!--more-->
>
> I risultati ottenuti in fase di analisi sono stati verificati sperimentalmente in modo esteso e l&#8217;algoritmo di base è stato migliorato al punto da diventare il metodo ideale per un gran numero di applicazioni pratiche.
>
> tratto da wikipedia

Per la sua estrema facilità è stato scelto in molte librerie di linguaggi, come il C, di implementare di base una funzione che effettui l&#8217;ordinamento del Quicksort&#8230; però il nostro professore di programmazione vuole vedere il codice sorgente :-)

## Codice C Quicksort

Eccolo qua:

<pre lang="c">#include &lt;stdio.h&gt;
#define MAX 20

stampavettore(int *vettore,int n)
{
 int i;

 for(i=0 ; i&lt;=n ; printf("%d ",vettore[i++]));
}

int riempivettore(int *vettore)
{
 int i;

 i=0;
 do {
 printf("inserire l'elemento %d dell'array('-1' per terminare): ",i+1);
 scanf("%d",vettore+i);
 } while (vettore[i++] != -1);
 return i-2;
}

void scambia(int *n1,int *n2)
{
 int temp;

 temp = *n1;
 *n1 = *n2;
 *n2 = temp;
}

int partiziona(int *vettore, int p, int r)
{
 int x = vettore[p];
 int i = p-1;
 int j = r+1;
 int itera = 1;

 do {
 for(; vettore[--j] &gt; x ;);
 for(; vettore[++i] &lt; x ;);

 if (i &lt; j)
 {
 scambia(&vettore[i],&vettore[j]);
 }
 else
 {
 itera = 0;
 }
 } while (itera);

return j;
}

void quicksort(int *vettore, int p, int r)
{
 int q;

 if (p &lt; r)
 {
 q = partiziona(vettore,p,r);
 quicksort(vettore,p,q);
 quicksort(vettore,q+1,r);
 }
}

main()
{
 int vettore[MAX];
 int n; /*numero di elementi*/

 n=riempivettore(vettore);

 quicksort(vettore,0,n);

 stampavettore(vettore,n);
}</pre>

## Caratteristiche del Quicksort

<table border="0">
  <tr>
    <th>
      Struttura dati
    </th>

    <td>
      Variabile
    </td>
  </tr>

  <tr>
    <th>
      Caso pessimo temporalmente
    </th>

    <td>
      <span class="texhtml">Θ(<em>n</em><sup>2</sup>)</span>
    </td>
  </tr>

  <tr>
    <th>
      Caso ottimo temporalmente
    </th>

    <td>
      <span class="texhtml">Θ(<em>n</em>log<em>n</em>)</span>
    </td>
  </tr>

  <tr>
    <th>
      Caso medio temporalmente
    </th>

    <td>
      <span class="texhtml">Θ(<em>n</em>log<em>n</em>)</span> confronti
    </td>
  </tr>

  <tr>
    <th>
      Caso pessimo spazialmente
    </th>

    <td>
      Dipende dalle implementazioni
    </td>
  </tr>

  <tr>
    <th>
      Ottimale
    </th>

    <td>
      Spesso
    </td>
  </tr>
</table>
