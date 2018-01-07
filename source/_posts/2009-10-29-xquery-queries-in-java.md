---
title: XQuery queries in Java
layout: post
comments: true
categories:
  - programming
tags:
  - basex
  - java
  - xml
  - xquery
---
<p style="text-align: justify;">
  XQuery, una abbrevazione per XML Query Language, è un linguaggio di programmazione specificato dal W3C e destinato ad interrogare documenti e basi di dati XML. Questo perché XML si sta proponendo come la tecnologia per rimpiazzare i vecchi DBMS relazionali :-)
</p>

<p style="text-align: justify;">
  Il w3c ha definito il linguaggio XQuery 1.0; usa la sintassi delle espressioni di XPath  2.0, con l&#8217;aggiunta delle cosiddette espressioni FLWOR per la formulazione di query complesse. Il risultato è un linguaggio di programmazione funzionale, dichiarativo, con somiglianze con il vecchio SQL.
</p>

<p style="text-align: justify;">
  Per effettuare delle query xquery su un file XML possiamo usare delle librerie come BaseX e Saxon. Purtroppo attualmente Saxon non è un prodotto del tutto gratuito, quindi scegliamo di usare BaseX, un processore Xquery-XPath open source.
</p>

<p style="text-align: justify;">
  <!--more-->In realtà BaseX, oltre ad essere utlilizzabile come libreria all&#8217;interno del linguaggio Java, ci mette a disposizione un&#8217;interfaccia grafica dalla quale possiamo effettuare query su file XML ben formati arbitrari.
</p>

<h2 style="text-align: justify;">
  Primo esempio di query
</h2>

<p style="text-align: justify;">
  La prima cosa da fare è inserire i file jar di BaseX nel build path del nostro progetto; la seconda è assicurarsi di avere java 1.6 (non funziona con java 1.5) perché BaseX utilizza il package javax.xml.stream.
</p>

<p style="text-align: justify;">
  Questo è un sempio dove si esegue la query <strong>//li </strong>sul file &#8216;<strong>input</strong>&#8216;:
</p>

<pre lang="java">import javax.xml.xquery.XQConnection;
import javax.xml.xquery.XQDataSource;
import javax.xml.xquery.XQPreparedExpression;
import javax.xml.xquery.XQResultSequence;

public final class XQueryAPIExample {
 /** Database Driver. */
 static final String DRIVER = "org.basex.api.xqj.BXQDataSource";

 public static void main(final String[] args) throws Exception {

 // Gets the XQDataSource for the specified Driver.
 XQDataSource source = (XQDataSource) Class.forName(DRIVER).newInstance();

 // Creates an XQConnection
 XQConnection conn = source.getConnection();

 // Prepares the Expressionwith the Document and the Query.
 XQPreparedExpression expr = conn.prepareExpression("doc('input')//li");

 // Executes the XQuery query.
 XQResultSequence result = expr.executeQuery();

 // Gets all results of the execution.
 while(result.next()) {
 // Prints the results to the console.
 System.out.println(result.getItemAsString(null));
 }

 }
}</pre>

<p style="text-align: justify;">
  Questo esempio funziona solo se il file XML interrogato non dichiara nessun namespace.
</p>

<h2 style="text-align: justify;">
  Query in presenza di namespace
</h2>

<p style="text-align: justify;">
  Supponiamo adesso di interrogare un file XML con namespace&#8230; ad esempio un file in formato XML Mpeg-7 che usa i seguenti namespace:<br /> xmlns=&#8221;urn:mpeg:mpeg7:schema:2001&#8243;<br /> xmlns:mpeg7=&#8221;urn:mpeg:mpeg7:schema:2001&#8243;<br /> xmlns:xsi=&#8221;http://www.w3.org/2001/XMLSchema-instance&#8221;
</p>

<p style="text-align: justify;">
  Per far riconoscere i namespace dobbiamo dichiararli nel prologo della xquery in questo modo:<br /> declare default element namespace &#8220;urn:mpeg:mpeg7:schema:2001&#8221;<br /> declare  namespace mpeg7 = &#8220;urn:mpeg:mpeg7:schema:2001&#8221;<br /> declare  namespace xsi = &#8220;http://www.w3.org/2001/XMLSchema-instance&#8221;
</p>

<p style="text-align: justify;">
  Questo è il codice che esegue la query sul file file/video/extract.xml:
</p>

<pre lang="java">String prologoQuery = "" +
 "declare default element namespace \"urn:mpeg:mpeg7:schema:2001\"; " +
 "declare  namespace mpeg7 = \"urn:mpeg:mpeg7:schema:2001\"; " +
 "declare  namespace xsi = \"http://www.w3.org/2001/XMLSchema-instance\"; ";

 // Gets the XQDataSource for the specified Driver.
 XQDataSource source = (XQDataSource) Class.forName(DRIVER).newInstance();
 // Creates an XQConnection
 XQConnection conn = source.getConnection();
 // Prepares the Expressionwith the Document and the Query.
 //XQPreparedExpression expr = conn.prepareExpression("&lt;xml&gt;1 + 2 = { 1+2 }&lt;/xml&gt;/text()");
 //XQPreparedExpression expr = conn.prepareExpression("doc('file/video/20090201_video_15213221.xml')//meta");
 XQPreparedExpression expr = conn.prepareExpression(prologoQuery + " doc('file/video/extract.xml')//Name");

 // Executes the XQuery query.
 XQResultSequence result = expr.executeQuery();
 // Gets all results of the execution.
 while(result.next()) {
 //element = (org.w3c.dom.Element) result.getObject();
 System.out.println(result.getItemAsString(null));
 }</pre>

<p style="text-align: justify;">
  Nella riga 18 è commentato un altro modo per usare gli oggetti restiuiti dalla query, che ci restituisce il risultato come elementi della struttura DOM del file XML.
</p>
