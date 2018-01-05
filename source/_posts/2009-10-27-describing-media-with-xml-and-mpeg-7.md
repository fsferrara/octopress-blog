---
comments: true
title: Describing media with XML and MPEG-7
date: 2009-10-27T01:17:43+00:00
author: fsferrara
layout: post
guid: http://www.fsferrara.com/?p=119
permalink: /describing-media-with-xml-and-mpeg-7/
categories:
  - Programming
tags:
  - MPEG-7
  - XML
---
<p class="western">
  La diffusione delle connessioni a banda larga ha agevolato la diffusione di audio e video via web: un esempio eclatante è YouTube! Ma riuscire a trovare un video particolare tra la grossa quantità di dati multimediali sul web è un compito arduo: il valore del dato multimediale dipende da quanto è agevole trovarlo, gestirlo, ed accedere.
</p>

<p style="margin-bottom: 0cm;">
  Per gestire questa grossa quantità di dati multimediali, sia da parte degli utenti, sia da parte dei sistemi automatici, ci aiuta Mpeg-7: uno standard nato per codificare i contenuti multimediali attraverso la definizione di metadati sui dati multimediali.
</p>

<p style="margin-bottom: 0cm;">
  I precedenti standard Mpeg-1 (1992), Mpeg-2 (1994), e Mpeg-4 (1999) riguardano la codifica del video. Nel 2001 è stato definito Mpeg-7 che non definisce il modo di codificare un video, ma riguarda la sua metataggatura attraverso un linguaggio XML.<br /> Perché 7? Mpeg-7 permette di definire metadati sui video codificati con Mpeg 1, 2, e 4. Siccome 4+2+1=7, nasce il nome Mpeg-7.
</p>

<p style="margin-bottom: 0cm;">
  <!--more-->
</p>

<p style="margin-bottom: 0cm;">
  Notiamo come non è stato nominato Mpeg-3, lo standard per i famosissimi mp3 :) . In realtà questo standard non esiste, ma il nome Mpeg-3 è usato per riferirsi alla parte audio di Mpeg-2.
</p>

## Metadati {.western}

<p style="margin-bottom: 0cm;">
  I metadati associati ad un video permettono di descrivere cosa c&#8217;è nel video. Mpeg-7 permette descrizioni sia a basso livello (caratteristiche del segnale, come il colore di un oggetto), sia ad alto livello (informazioni semantiche, come la scena di un goal in una partita di calcio).<br /> Un esempio di file XML in formato Mpeg-7 contenente la descrizione di un video di una notizia è:
</p>

<pre lang="xml">&lt;?xml version="1.0" encoding="UTF-8" standalone="no"?&gt;
 &lt;!--Metadati generati automaticamente dall'applicazione--&gt;
&lt;Mpeg7 xmlns="urn:mpeg:mpeg7:schema:2001" xmlns:mpeg7="urn:mpeg:mpeg7:schema:2001"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xsi:schemaLocation="urn:mpeg:mpeg7:schema:2001 Mpeg7-2001.xsd"&gt;
 &lt;Description xsi:type="ContentEntityType"&gt;
 &lt;MultimediaContent xsi:type="VideoType"&gt;
 &lt;Video&gt;
 &lt;MediaInformation&gt;
 &lt;MediaProfile&gt;
 &lt;MediaFormat&gt;
 &lt;Content href="MPEG7ContentCS" /&gt;
 &lt;FileFormat href="urn:mpeg:mpeg7:cs:FileFormatCS:2001:3"&gt;
 &lt;Name&gt;mpeg&lt;/Name&gt;
 &lt;/FileFormat&gt;
 &lt;FileSize&gt;17333073&lt;/FileSize&gt;
 &lt;VisualCoding&gt;
 &lt;Format colorDomain="color"
 href="urn:mpeg:mpeg7:cs:VisualCodingFormatCS:2001:1" /&gt;
 &lt;Frame height="576" rate="8000" width="720" /&gt;
 &lt;/VisualCoding&gt;
 &lt;/MediaFormat&gt;
 &lt;MediaInstance id="v20090201_video_15213221"&gt;
 &lt;InstanceIdentifier /&gt;
 &lt;MediaLocator&gt;
 &lt;MediaUri&gt;20090201_video_15213221.mov&lt;/MediaUri&gt;
 &lt;/MediaLocator&gt;
 &lt;/MediaInstance&gt;
 &lt;/MediaProfile&gt;
 &lt;/MediaInformation&gt;
 &lt;CreationInformation&gt;
 &lt;Creation&gt;
 &lt;Title&gt;Obama: presto un piano per famiglie Usa per tagliare costi
 mutui&lt;/Title&gt;
 &lt;Abstract&gt;
 &lt;FreeTextAnnotation&gt;
 Presidente cerca arginare effetti devastante crisi economica
 &lt;/FreeTextAnnotation&gt;
 &lt;StructuredAnnotation&gt;
 &lt;When&gt;
 &lt;Name&gt;1 Feb 2009&lt;/Name&gt;
 &lt;/When&gt;
 &lt;/StructuredAnnotation&gt;
 &lt;/Abstract&gt;
 &lt;Creator&gt;
 &lt;Role href="urn:mpeg:mpeg7:cs:RoleCS:2001:producer"&gt;
 &lt;Name&gt;Red&lt;/Name&gt;
 &lt;/Role&gt;
 &lt;Agent xsi:type="OrganizationType"&gt;
 &lt;Name&gt;Apcom&lt;/Name&gt;
 &lt;/Agent&gt;
 &lt;/Creator&gt;
 &lt;CreationCoordinates&gt;
 &lt;Location&gt;
 &lt;Name&gt;milano&lt;/Name&gt;
 &lt;/Location&gt;
 &lt;Date&gt;
 &lt;TimePoint&gt;2009-02-01T15:21:32&lt;/TimePoint&gt;
 &lt;/Date&gt;
 &lt;/CreationCoordinates&gt;
 &lt;CopyrightString&gt;TMNews&lt;/CopyrightString&gt;
 &lt;/Creation&gt;
 &lt;Classification&gt;
 &lt;Genre href="urn:mpeg:TVAnytime_v0.1ContentCS:3.14"&gt;
 &lt;Name&gt;est&lt;/Name&gt;
 &lt;/Genre&gt;
 &lt;MediaReview&gt;
 &lt;Rating&gt;
 &lt;RatingValue&gt;0.0&lt;/RatingValue&gt;
 &lt;RatingScheme best="5" style="higherBetter" worst="0"&gt;
 &lt;Name&gt;Overall&lt;/Name&gt;
 &lt;/RatingScheme&gt;
 &lt;/Rating&gt;
 &lt;/MediaReview&gt;
 &lt;/Classification&gt;
 &lt;RelatedMaterial&gt;
 &lt;MediaLocator&gt;
 &lt;MediaUri&gt;20090201_video_17483840.mov&lt;/MediaUri&gt;
 &lt;/MediaLocator&gt;
 &lt;/RelatedMaterial&gt;
 &lt;RelatedMaterial&gt;
 &lt;MediaLocator&gt;
 &lt;MediaUri&gt;20090201_video_18024720.mov&lt;/MediaUri&gt;
 &lt;/MediaLocator&gt;
 &lt;/RelatedMaterial&gt;
 &lt;RelatedMaterial&gt;
 &lt;MediaLocator&gt;
 &lt;MediaUri&gt;20090201_video_18094945.mov&lt;/MediaUri&gt;
 &lt;/MediaLocator&gt;
 &lt;/RelatedMaterial&gt;
 &lt;RelatedMaterial&gt;
 &lt;MediaLocator&gt;
 &lt;MediaUri&gt;20090201_video_18153193.mov&lt;/MediaUri&gt;
 &lt;/MediaLocator&gt;
 &lt;/RelatedMaterial&gt;
 &lt;RelatedMaterial&gt;
 &lt;MediaLocator&gt;
 &lt;MediaUri&gt;20090202_video_13033231.mov&lt;/MediaUri&gt;
 &lt;/MediaLocator&gt;
 &lt;/RelatedMaterial&gt;
 &lt;RelatedMaterial&gt;
 &lt;MediaLocator&gt;
 &lt;MediaUri&gt;20090202_video_13094131.mov&lt;/MediaUri&gt;
 &lt;/MediaLocator&gt;
 &lt;/RelatedMaterial&gt;
 &lt;RelatedMaterial&gt;
 &lt;MediaLocator&gt;
 &lt;MediaUri&gt;20090202_video_16491593.mov&lt;/MediaUri&gt;
 &lt;/MediaLocator&gt;
 &lt;/RelatedMaterial&gt;
 &lt;RelatedMaterial&gt;
 &lt;MediaLocator&gt;
 &lt;MediaUri&gt;20090202_video_17042673.mov&lt;/MediaUri&gt;
 &lt;/MediaLocator&gt;
 &lt;/RelatedMaterial&gt;
 &lt;/CreationInformation&gt;
 &lt;UsageInformation&gt;
 &lt;Availability id="onDemand"&gt;
 &lt;InstanceRef href="MPEG7PublicationTypeCS:4" /&gt;
 &lt;Dissemination&gt;
 &lt;Format href="MPEG7PublicationTypeCS:4"&gt;
 &lt;Name&gt;Internet&lt;/Name&gt;
 &lt;/Format&gt;
 &lt;Location&gt;
 &lt;Region&gt;it&lt;/Region&gt;
 &lt;/Location&gt;
 &lt;/Dissemination&gt;
 &lt;/Availability&gt;
 &lt;UsageRecord&gt;
 &lt;AvailabilityRef idref="onDemand" /&gt;
 &lt;Audience&gt;0&lt;/Audience&gt;
 &lt;/UsageRecord&gt;
 &lt;/UsageInformation&gt;
 &lt;MediaTime&gt;
 &lt;MediaTimePoint&gt;T00:00:00&lt;/MediaTimePoint&gt;
 &lt;MediaDuration&gt;PT0H0M29S&lt;/MediaDuration&gt;
 &lt;/MediaTime&gt;
 &lt;/Video&gt;
 &lt;/MultimediaContent&gt;
 &lt;MultimediaContent xsi:type="ImageType"&gt;
 &lt;Image&gt;
 &lt;MediaInformation&gt;
 &lt;MediaProfile&gt;
 &lt;MediaFormat&gt;
 &lt;Content href="urn:mpeg:mpeg7:cs:ContentCS:2001:2"&gt;
 &lt;Name&gt;visual&lt;/Name&gt;
 &lt;/Content&gt;
 &lt;FileFormat href="urn:mpeg:mpeg7:cs:FileFormatCS:2001:3"&gt;
 &lt;Name&gt;JPEG2000&lt;/Name&gt;
 &lt;/FileFormat&gt;
 &lt;FileSize&gt;12014&lt;/FileSize&gt;
 &lt;VisualCoding&gt;
 &lt;Format colorDomain="binary"
 href="urn:mpeg:mpeg7:cs:VisualCodingFormatCS:2001:1"&gt;
 &lt;Name&gt;JPEG2000&lt;/Name&gt;
 &lt;/Format&gt;
 &lt;Frame height="288" rate="0" width="360" /&gt;
 &lt;/VisualCoding&gt;
 &lt;/MediaFormat&gt;
 &lt;MediaInstance id="i20090201_video_15213221"&gt;
 &lt;InstanceIdentifier /&gt;
 &lt;MediaLocator&gt;
 &lt;MediaUri&gt;20090201_video_15213221.jpg&lt;/MediaUri&gt;
 &lt;/MediaLocator&gt;
 &lt;/MediaInstance&gt;
 &lt;/MediaProfile&gt;
 &lt;/MediaInformation&gt;
 &lt;CreationInformation&gt;
 &lt;Creation&gt;
 &lt;Title&gt;
 Foto
&lt;/Title&gt;
 &lt;Creator&gt;
 &lt;Role href="urn:mpeg:mpeg7:cs:RoleCS:AUTHOR"&gt;
 &lt;Name&gt;Red&lt;/Name&gt;
 &lt;/Role&gt;
 &lt;Agent xsi:type="OrganizationType"&gt;
 &lt;Name&gt;MPEG&lt;/Name&gt;
 &lt;/Agent&gt;
 &lt;/Creator&gt;
 &lt;/Creation&gt;
 &lt;/CreationInformation&gt;
 &lt;/Image&gt;
 &lt;/MultimediaContent&gt;
 &lt;/Description&gt;
&lt;/Mpeg7&gt;</pre>

<p style="margin-bottom: 0cm;">
  Mpeg-7 è un linguaggio XML, ossia usa XML per definire i metadati. In realtà un file Mpeg-7 non è altro che un file &#8216;.xml&#8217; associato ad uno o più oggetti multimediali. Quindi è possibile memorizzare i metadati indipendentemente dai video&#8230; ad esempio un possibile uso di Mpeg-7, è la costruzione di un database multimediale!
</p>

## Componenti di Mpeg-7 {.western}

<p style="margin-bottom: 0cm;">
  Lo standard Mpeg-7 è composta da quattro elementi fondamentali:
</p>

  * <p style="margin-bottom: 0cm;">
      Description Tools
    </p>

  * <p style="margin-bottom: 0cm;">
      Descriptor
    </p>

  * <p style="margin-bottom: 0cm;">
      Description Scheme
    </p>

  * <p style="margin-bottom: 0cm;">
      DDL – Description Definition<br /> Language
    </p>

  * <p style="margin-bottom: 0cm;">
      System Tool
    </p>

<p style="margin-bottom: 0cm;">
  I metadati di un oggetto multimediale saranno descritti usando i &#8216;Description Tools&#8217;.<br /> I &#8216;Description Tools&#8217; a loro volta fanno uso del &#8216;Description Definition Language&#8217; (DDL) che è una estensione di XML Schema proprio per Mpeg-7.<br /> I &#8216;System Tool&#8217; non riguardano la definizione di metadati, ma la loro rappresentazione e trasmissione. Quindi il file XML è prodotto utilizzando solo &#8216;Description Tools&#8217; e &#8216;DDL&#8217;, e poi questo file XML può essere diffuso utilizzando le tecniche dei &#8216;System Tools&#8217;.
</p>

### Description Definition Language (DDL) {.western}

<p style="margin-bottom: 0cm;">
  Il DDL è basato su XML Schema Language e ne rappresenta una sorta di estensione orientata al multimedia. In particolare XML Schema non è stato progettato per le descrizioni di contenuti audio/video e necessita quindi di tipi di dato per array e matrici, e tipo di dato per gestire il tempo (BasicTimePoint e BasicDuration).
</p>

<p style="margin-bottom: 0cm;">
  Ad esempio la definizione di TimeType è:
</p>

<pre lang="XML">&lt;!-- Definition of Time datatype --&gt;
&lt;complexType name="TimeType"&gt;
 &lt;sequence&gt;
 &lt;choice&gt;
 &lt;element name="TimePoint" type="mpeg7:TimePointType" /&gt;
 &lt;element name="RelTimePoint" type="mpeg7:RelTimePointType" /&gt;
 &lt;element name="RelIncrTimePoint" type="mpeg7:RelIncrTimePointType" /&gt;
 &lt;/choice&gt;
 &lt;choice minOccurs="0"&gt;
 &lt;element name="Duration" type="mpeg7:durationType" /&gt;
 &lt;element name="IncrDuration" type="mpeg7:IncrDurationType" /&gt;
 &lt;/choice&gt;
 &lt;/sequence&gt;
&lt;/complexType&gt;

&lt;!-- Definition of TimePoint datatype --&gt;
&lt;simpleType name="TimePointType"&gt;
 &lt;restriction base="mpeg7:basicTimePointType"&gt;
 &lt;pattern
 value="(\-?\d+(\-\d{2}(\-\d{2})?)?)?(T\d{2}(:\d{2}(:\d{2} (:\d+)?)?)?)?(F\d+)?(\-|\+\d{2}:\d{2})?" /&gt;
 &lt;/restriction&gt;
&lt;/simpleType&gt;

&lt;!-- Definition of duration datatype --&gt;
&lt;simpleType name="durationType"&gt;
 &lt;restriction base="mpeg7:basicDurationType"&gt;
 &lt;pattern
 value="\-?P(\d+D)?(T(\d+H)?(\d+M)
 ?(\d+S)?(\d+N)?)?( \d+F)?((\-|\+)\d{2}:\d{2}Z)?" /&gt;
 &lt;/restriction&gt;
&lt;/simpleType&gt;</pre>

<p style="margin-bottom: 0cm;">
  Usando queste definizioni di tipo contenute nella DDL, siamo in grado di descrivere il fatto che un certo filmato rappresenta un evento iniziato il 16 ottobre 2002 alle ore 17:00 in un paese con GTM+1, e dura 10 giorni, con questo codice:
</p>

<pre lang="XML">&lt;Time&gt;
  &lt;TimePoint&gt;2002-10-16T17:00+01:00&lt;/TimePoint&gt;
  &lt;Duration&gt;P10D&lt;/Duration&gt;
&lt;/Time&gt;</pre>

<p style="margin-bottom: 0cm;">
  Ovviamente il DDL, oltre ai tipi qui introdotti (TimeType, TimePointType, e durationType), contiene molte altre definizioni che per brevità non tratteremo.
</p>

### Description Tools {.western}

<p style="margin-bottom: 0cm;">
  I Description Tools comprendono &#8216;Descriptor&#8217; e &#8216;Descriptor Schemes&#8217; che preferisco non distinguere e trattarli insieme, raggruppandoli in base alle loro funzionalità:
</p>

  * <p style="margin-bottom: 0cm;">
      <strong>Schema and Basic Elements</strong>:<br /> forniscono tutti i tipi di dato utilizzati nelle descrizioni, e la<br /> loro corrispondenza con i tag utilizzati in Mpeg-7;
    </p>

  * <p style="margin-bottom: 0cm;">
      <strong>Content Description</strong>:<br /> rappresentazione dell&#8217;informazione audio/video sia a livello<br /> strutturale (basso livello), sia a livello semantico (alto livello);
    </p>

  * <p style="margin-bottom: 0cm;">
      <strong>Content Management</strong>:<br /> permette di descrivere caratteristiche come creazione, formato, ed<br /> uso del materiale multimediale;
    </p>

  * <p style="margin-bottom: 0cm;">
      <strong>Content Organization</strong>:<br /> Permette di gestire collezioni di materiale multimediale: si possono<br /> usare questi tool per implementare una base di dati XML di<br /> informazioni su materiale multimediale;
    </p>

  * <p style="margin-bottom: 0cm;">
      <strong>Navigation and Access</strong>:<br /> aiutano l&#8217;accessibilità al file multimediale;
    </p>

  * <p style="margin-bottom: 0cm;">
      <strong>User Interaction</strong>:<br /> permettono di memorizzare le preferenze dell&#8217;utente.
    </p>

Con i Description Tools siamo in grado di produrre due tipi di descrizioni Mpeg-7 valide: le &#8220;Complete Descriptions&#8221; che descrivono interamente un materiale multimediale come un video (l&#8217;esempio di file xml Mpeg-7 di questo articolo corrisponde ad una Complete Description perchè descrive completamente il video), e le &#8220;Descriptions Units&#8221; che non sono descrizioni intere ma dei componenti che possono far parte di una Complete Description.

## Conclusioni {.western}

<p style="margin-bottom: 0cm;">
  Non si è trattata la parte dei System Tools, inoltre della parte dei Description Tool si è data una semplice descrizione generale. I Description Tool sono la parte più corposa dello standard Mpeg-7, e studiarli tutti può richiedere tempo. Si suggerisce a tal proposito di utilizzare i documenti ufficiali dello standard o l&#8217;utilissima guida di Chiariglione all&#8217;indirizzo http://www.chiariglione.org/mpeg/ .
</p>
