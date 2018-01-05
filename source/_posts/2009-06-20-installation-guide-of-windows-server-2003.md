---
comments: true
title: Installation guide of Windows Server 2003
date: 2009-06-20T01:08:47+00:00
author: fsferrara
layout: post
guid: http://www.fsferrara.com/?p=112
permalink: /installation-guide-of-windows-server-2003/
categories:
  - System Administration
tags:
  - tuning
  - windows server
---
Successore di Windows 2000, Microsoft Windows Server 2003 (Nome in codice Whistler Server, o anche Windows NT 5.2 o ancora Windows .NET Server) (2003) è una tappa della evoluzione della serie server dei sistemi operativi di Microsoft. Il lancio è avvenuto il 24 aprile 2003.

Windows Server 2003 è basato sulla provata stabilità di Windows 2000 Server e la compatibilità con altre caratteristiche di Windows XP.

Questa guida all&#8217;installazione e configurazione di Windows Server 2003 è rivolta ai sistemisti alle prime armi, oppure a chi vuole costrure il proprio server a casa :)

Sarà copera la parte della configurazione Hardware di un buon server; successivamente sarà indicato come configurare il Windows Server 2003 appena dopo l&#8217;installazione

<!--more-->

## Installazione Windows Server 2003

Anche se stiamo in italia, in ambito server installare sempre la versione inglese del sistema&#8230; questo ci può creare problemi per la rappresentazione delle date, ma ci semplifica la gestione: installare sempre gli altri pacchetti in inglese!!!

## Hardware

Un pò di buon senso&#8230;

  * server web => molta RAM
  * server di file => molto spazio HD

Per piccole/medie imprese va bene un bi-processore. Per grossi server ci sono macchine a 4 processori: ITANIUM, OPTERON (AMD), XEON (INTEL)

Componenti interni fondamentali per il fault-tollerance:

&#8211; Alimentatore interno ridondande,

&#8211; Disk-array RAID:

&#8211; RAID 0, numero pari di dischi (mirroring)

&#8211; RAID 5, numero dispari di dischi + 1 di ripresa a caldo

Sono consigliabili minimo due interfacce di rete: 1 per la rete interna, e 1 per la rete esterna (internet).

Possibilemente schede di rete Gigabit

I moduli di RAM devono essere affidabili: **ECC** (Error Correction Code).

## Preparativi

Partizionare il disco&#8230; almeno una partizione per il sistema operativo e una per i dati.

Un partizionamento professionale prevede quattro partizioni: System, Swap File, User Data, RIS Partition

Notare che i cilindri esterni del disco sono quelli letti più velocemente&#8230; conviene posizionale in questi posti la partizione di swap. Inoltre è buona norma fare la partiziona del sistema operativo (System) quanto più piccola possibile.

## Configurazione di Base

Innanzitutto fare tutti gli aggiornamenti, installare le utility (bginfo, siw, ecc&#8230;), ed evitare sempre di usare Internet Explorer per scopi personali.

### Menu e Desktop

Mettere il menu classico, oppure dalle impostazioni avanzate del desktop permettere di visualizzare le classiche icone sul desktop.

### File temporanei

Bisogna unificare la cartella dei file temporanei, quindi:

1) Click destro su &#8220;My Computer&#8221; -> &#8220;Proprierties&#8221; -> tab &#8220;Advanced&#8221;

2) Modificare le variabili TMP e TEMP in modo che puntino alla stessa directory sul disco&#8230; ad esempio C:\Temp

### File di swap

Fissare le dimensioni del file di swap in modo che variazioni del file non portino ad un&#8217;eccessiva frammentazione. Ad esempio:

-> Initial size (MB): 2048

-> Maxium size (MB): 2048

### Effetti grafici

Eliminare gli effetti grafici:

-> Click destro sul Desktop -> &#8220;Proprierties&#8221; -> &#8220;Appareance ed Effects&#8221;

### Monitor

Configurare gli Hertz del monitor a 60Hz. In questo modo non avremmo problemi di visualizzazione nel caso operiamo da vecchi terminali.

### Aggiornamenti automatici

Per avere il totale controllo della macchina e&#8217; bene disabilitare gli aggiornamenti automatici, in modo che **Download the updates automatically and notify me when they are ready to be installed**.
