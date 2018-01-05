---
comments: true
title: Java implementation of the Ackermann function
date: 2009-11-29T01:24:14+00:00
author: fsferrara
layout: post
guid: http://www.fsferrara.com/?p=121
permalink: /java-implementation-of-the-ackermann-function/
categories:
  - Programming
tags:
  - ackermann
  - computability
  - Java
---
Wilhelm Friedrich Ackermann (29/3/1896 – 24/12/1962) was a German mathematician best known for the Ackermann function, an important example in the theory of computation.

La funzione di Ackermann è una funzione f(x,y,z) che ha come dominio l&#8217;insieme delle terne di numeri naturali e come codominio i numeri naturali.

Essa è un esempio di funzione ricorsiva che non è primitiva ricorsiva poiché cresce più velocemente di qualsiasi funzione ricorsiva primitiva.

<!--more--><figure id="attachment_122" style="max-width: 300px" class="wp-caption alignnone">

[<img class="size-medium wp-image-122" src="http://www.fsferrara.com/wp-content/uploads/2013/10/ackermann-300x54.png" alt="Ackermann function description" width="300" height="54" srcset="http://www.fsferrara.com/wp-content/uploads/2013/10/ackermann-300x54.png 300w, http://www.fsferrara.com/wp-content/uploads/2013/10/ackermann.png 477w" sizes="(max-width: 300px) 100vw, 300px" />](http://www.fsferrara.com/wp-content/uploads/2013/10/ackermann.png)<figcaption class="wp-caption-text">Ackermann function description</figcaption></figure>

Qui il codice java che implementa questa funzione:

<span style="text-decoration: underline;">Ackermann.java</span>

<pre lang="java">public class Ackermann {

 static long count = 0;

 private static long h(long m, long n) {

  count++;

  if (m == 0) {
   return n + 1;
  }
  if (n == 0) {
   return h(m-1, 1);
  }

  return h(m-1, h(m,n-1) );
 }

 private static long ack(long n) {
  return h(n, n);
 }

 public static void main(String[] args) {

  if (args.length != 1) {
   System.out.println("usage: Ackermann &lt;number&gt;\n\twhere number is a positive integer");
   System.exit(1);
  }

  long n = Long.valueOf(args[0]);

  count = 0;
  long retValue = ack(n);  
  System.out.println("ack(" + n + ") = " + retValue + " [recursive calls = "+ count +"]");

  System.exit(0);
 }

}</pre>

Il meccanismo di calcolo della funzione è estremamente semplice quanto pesante dal punto di vista computazionale. Questi sono i risultati ottenuti:

  * ack(0) = **1**  [recursive calls = **1**]
  * ack(1) = **3**  [recursive calls = **4**]
  * ack(2) = **7**  [recursive calls = **27**]
  * ack(3) = **61** [recursive calls = **2432**]

Non riesco a calcolare ack(4) causa stack overflow (Exception in thread &#8220;main&#8221; java.lang.StackOverflowError).
