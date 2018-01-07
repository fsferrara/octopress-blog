---
title: C implementation of Heap sort algorithm
layout: post
comments: true
categories:
  - programming
tags:
  - c
  - sort
---
L&#8217; heapsort è un algoritmo di ordinamento iterativo ed in-place proposto da Williams nel 1964, che si basa su strutture dati ausiliarie.

> L&#8217; heapsort per eseguire l&#8217;ordinamento, utilizza una struttura chiamata heap (mucchio); un heap è rappresentabile con un albero binario in cui tutti i nodi seguono una data proprietà, detta priorità. Esso è completo almeno fino al penultimo livello dell&#8217;albero e ad ogni nodo corrisponde uno ed un solo elemento.
>
> In uno heap decrescente (utilizzato per ordinare ad esempio un array in senso crescente) ogni nodo padre contiene un valore maggiore o uguale a quello dei suoi due figli diretti, di conseguenza risulterà maggiore anche di tutti i nodi che si trovano nel sottoalbero di cui esso è la radice; questo non implica affatto che nodi a profondità maggiore contengano valori minori di quelli a profondità minore.
>
> Quindi in ogni istante, in un heap decrescente, la radice contiene il valore maggiore.
>
> Questa struttura è molto usata, in particolare, per l&#8217;ordinamento di array.
>
> In questo caso si considera come radice l&#8217;elemento iniziale di indice 1; inoltre i figli di un nodo con indice j, avranno indice rispettivamente 2j, quello sinistro, 2j+1 quello destro.
>
> <!--more-->Per comprendere meglio il funzionamento dell&#8217;algoritmo è bene capire che gli elementi che si trovano nella seconda metà dell&#8217;array rappresenteranno foglie dello heap e quindi esse saranno già al loro posto giusto; non vi è infatti alcun elemento dopo di esse.
>
> &#8230;tratto da wikipedia

## Implementazione Iterativa di Heap Sort

L&#8217;algoritmo che ordina in senso crescente inizia creando uno heap decrescente. Per ogni iterazione si copia la radice (primo elemento dell&#8217;array) in fondo all&#8217;array stesso, eseguendo uno scambio di elementi. L&#8217;algoritmo poi ricostruisce uno heap di n &#8211; 1 elementi spostando verso il basso la nuova radice, e ricomincia con un altro scambio (tra il primo elemento dell&#8217;array e quello in posizione n &#8211; 1), eseguendo un ciclo che considera array di dimensione progressivamente decrescente.

<pre lang="c">#include &lt;stdio.h&gt;
#define MAX 20

int sinistro(int i)
{
 return 2*i+1;
}

int destro(int i)
{
 return 2*i+2;
}

int padre(int i)
{
 return (int)(i-1/2);
}

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

void heapify(int *vettore, int i,int heapsize)
{
 int l,r,maggiore,violazione=1;

 while (violazione)
 {
 l = sinistro(i);
 r = destro(i);

 if ((l &lt;= heapsize) && (vettore[l] &gt; vettore[i]))
 {
 maggiore = l;
 }
 else
 {
 maggiore = i;
 }

 if ((r &lt;= heapsize) && (vettore[r]&gt;vettore[maggiore]))
 {
 maggiore = r;
 }
 if (maggiore != i)
 {
 scambia(&vettore[i],&vettore[maggiore]);
 i=maggiore;
 }
 else
 {
 violazione = 0;
 }
 }
}

void buildheap(int *vettore,int heapsize,int n)
{
 int i;

 for (i=(int)(n/2) ; i&gt;=0 ; i--)
 {
 heapify(vettore,i,heapsize);
 }
}

heapsort(int *vettore,int n)
{
 int i,heapsize;

 heapsize=n;
 buildheap(vettore,heapsize,n);
 for (i=n ; i&gt;0 ; i--)
 {
 scambia(&vettore[0],&vettore[i]);
 heapsize--;
 heapify(vettore,0,heapsize);
 }
}

main()
{
 int vettore[MAX];
 int n; /*numero di elementi*/

 n=riempivettore(vettore);

 heapsort(vettore,n);

 stampavettore(vettore,n);
}</pre>

Si può dimostrare che la complessità asintotica massima dell&#8217;heap sort è O(nlogn). Tuttavia, in generale (e soprattutto per array quasi ordinati) altri algoritmi con la medesima complessità asintotica, per esempio quick sort o merge sort, ottengono migliori prestazioni. Per array di piccole dimensioni è addirittura più veloce l&#8217;insertion sort nonostante abbia una complessità di O(n^2))
