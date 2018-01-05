---
comments: true
title: Windows-Linux commands cheat-sheet
date: 2009-07-01T20:58:49+00:00
author: fsferrara
layout: post
guid: http://www.fsferrara.com/?p=60
permalink: /windows-linux-commands-cheat-sheet/
categories:
  - System Administration
tags:
  - dos
  - linux
  - ms-dos
  - shell
  - unix
  - windows
---
In un sistema operativo, una shell (o terminale) è un programma che permette agli utenti di comunicare con il sistema e di avviare altri programmi. È una delle componenti principali di un sistema operativo, insieme al kernel. La shell è l&#8217;ambiente di lavoro attraverso il quale è possibile impartire al computer comandi, richiedendo l&#8217;esecuzione di programmi.

Esistono molti tipi di shell; quando si parla semplicemente di &#8220;shell&#8221;, o anche di &#8220;terminale&#8221;, si intende di solito una shell testuale con cui l&#8217;utente interagisce attraverso un terminale o un emulatore di terminale.

<!--more-->



Una shell testuale è un programma dotato di un&#8217;interfaccia a riga di comando, che viene eseguito all&#8217;interno di un terminale testuale. L&#8217;utente digita un comando, ovvero richiede l&#8217;esecuzione di un programma, e il programma eseguito può interagire con l&#8217;utente e/o mostrare dati sul terminale.

Una delle più note shell testuali è il tradizionale &#8220;prompt dei comandi&#8221;, ben noto a quanti hanno familiarità con i sistemi operativi DOS (MS-DOS, DR-DOS, FreeDOS). Per gli utenti di MS-DOS e di alcuni dei sistemi Microsoft Windows la shell è il programma command.com. Anche i sistemi della famiglia Windows NT dispongono di una shell testuale, il programma cmd.exe.

Nei sistemi operativi Unix e Unix-like esistono diverse shell testuali; tra le più note vi sono sicuramente Bash (Bourne-Again Shell) e la Korn shell, ma ne esistono altre come la C shell, con un insieme di funzionalità e caratteristiche di base in comune.

Sono inoltre presenti potenti strumenti per collegare tra loro diversi programmi per svolgere compiti complessi, come le pipe e la redirezione. I programmi Unix più propensi ad essere collegati in questo modo sono detti filtri.

Le moderne shell testuali posseggono diverse funzionalità ergonomiche, tra le quali:

* la cronologia dei comandi eseguiti (o command history), che permette di ripetere gli ultimi comandi digitati;

* il completamento dei comandi (o completion), che permette di completare automaticamente nomi di programmi e di file

* il job control, che permette di avviare in background più programmi o di sospenderli temporaneamente.

Le shell testuali dei sistemi Unix integrano un linguaggio di scripting con il quale è possibile scrivere veri e propri programmi che possono ad esempio automatizzare le operazioni di amministrazione di sistema, semplificandola. La sintassi di tale linguaggio è un&#8217;estensione di quella usata interattivamente, per cui chi è familiare con l&#8217;uso interattivo della shell trova facile e naturale creare degli script.

Alcune delle funzionalità delle shell dei sistemi Unix sono state riprese in varia misura anche dalle shell testuali per i sistemi Microsoft Windows&#8230; Un utente che passa a Linux ha spesso bisogno di &#8220;tradurre&#8221; i comandi ms-dos in comandi per la shell bash. Bene&#8230; a me è capitato l&#8217;inverso, dopo 5 anni di utilizzo della shell Linux mi è capitato di gestire un server Windows 2003, e non conoscevo i comandi!!!

Per questo ho letto un manuale, ed ho scoperto che possiamo trovare comandi simili nei due ambienti; eccoli riportati in tabella:

<table border="1" width="100%" cellspacing="1" cellpadding="1">
  <tr align="center">
    <td>
      <strong>Descrizione</strong>
    </td>

    <td>
      <strong>Windows/Dos</strong>
    </td>

    <td>
      <strong>Linux</strong>
    </td>
  </tr>

  <tr>
    <td>
      Listato dettagliato dei file della directory corrente
    </td>

    <td>
      DIR
    </td>

    <td>
      ls -l
    </td>
  </tr>

  <tr>
    <td>
      Listato dei file della directory corrente
    </td>

    <td>
      DIR /W
    </td>

    <td>
      ls
    </td>
  </tr>

  <tr>
    <td>
      Crea una directory Pippo
    </td>

    <td>
      MD Pippo
    </td>

    <td>
      mkdir Pippo
    </td>
  </tr>

  <tr>
    <td>
      Cambia la directory corrente in ./Pippo
    </td>

    <td>
      CD Pippo
    </td>

    <td>
      cd Pippo
    </td>
  </tr>

  <tr>
    <td>
      Rimuove la directory Pippo (solo se vuota)
    </td>

    <td>
      RD Pippo
    </td>

    <td>
      rmdir Pippo
    </td>
  </tr>

  <tr>
    <td>
      Copia tutti i file nella directory Prova
    </td>

    <td>
      COPY *.* \Prova
    </td>

    <td>
      cp * /Prova
    </td>
  </tr>

  <tr>
    <td>
      Copia ricorsivamente tutti i file nella directory Prova
    </td>

    <td>
      XCOPY *.* \PROVA /E /S
    </td>

    <td>
      cp -dpR * /prova
    </td>
  </tr>

  <tr>
    <td>
      Rinomina Atricolo in Lettera
    </td>

    <td>
      REN Articolo Lettera
    </td>

    <td>
      mv Articolo Lettera
    </td>
  </tr>

  <tr>
    <td>
      Muove tutti i file nella directory Prova
    </td>

    <td>
      MOVE *.* \PROVA
    </td>

    <td>
      mv * /prova
    </td>
  </tr>

  <tr>
    <td>
      Cancella il file Articolo
    </td>

    <td>
      DEL Articolo
    </td>

    <td>
      rm Articolo
    </td>
  </tr>

  <tr>
    <td>
      Cancella ricorsivamente una directory (non incluso in windows xp e 2003)
    </td>

    <td>
      DELTREE Temp
    </td>

    <td>
      rm -R Temp
    </td>
  </tr>

  <tr>
    <td>
      Visualizza il contenuto di Lettera
    </td>

    <td>
      TYPE Lettera
    </td>

    <td>
      cat Lettera
    </td>
  </tr>

  <tr>
    <td>
      Visualizza il contenuto di Lettera dividendolo per schermate
    </td>

    <td>
      TYPE LETTERA | MORE
    </td>

    <td>
      cat lettera | more
    </td>
  </tr>

  <tr>
    <td>
      Aiuto sui comandi
    </td>

    <td>
      HELP HELP
    </td>

    <td>
      man man
    </td>
  </tr>

  <tr>
    <td>
      Formatta un floppy
    </td>

    <td>
      FORMAT A: /N:18 /T:80
    </td>

    <td>
      fdformat /dev/fd0u1440
    </td>
  </tr>

  <tr>
    <td>
      Copia un floppy in un altro usando due drive
    </td>

    <td>
      DISKCOPY A: B:
    </td>

    <td>
      cp /dev/fd0 /dev/fd1
    </td>
  </tr>

  <tr>
    <td>
      Copia un floppy in un altro usando un solo drive
    </td>

    <td>
      DISKCOPY A: A:
    </td>

    <td>
      cp /dev/fd0 /tmp/pippo ; cp /tmp/pippo /dev/fd0
    </td>
  </tr>

  <tr>
    <td>
      Carica le impostazione della tastiera italiana
    </td>

    <td>
      KEYB IT
    </td>

    <td>
      loadkeys it
    </td>
  </tr>

  <tr>
    <td>
      Pulisce lo schermo
    </td>

    <td>
      CLS
    </td>

    <td>
      clear
    </td>
  </tr>

  <tr>
    <td>
      Cerca la stringa &#8220;saluti&#8221; nel file Primo.doc
    </td>

    <td>
      FIND &#8220;saluti&#8221; Primo.doc
    </td>

    <td>
      grep &#8220;saluti&#8221; Primo.doc
    </td>
  </tr>

  <tr>
    <td>
      Partizionare e gestire i dischi
    </td>

    <td>
      DiskPart
    </td>

    <td>
      [c]fdisk
    </td>
  </tr>

  <tr>
    <td>
      Formattare le partizioni
    </td>

    <td>
      FORMAT
    </td>

    <td>
      mkfs.(tipo-fs)
    </td>
  </tr>

  <tr>
    <td>
      Cerca la stringa &#8220;saluti&#8221; in tutti i dile .doc
    </td>

    <td>
      FOR %A IN (*.DOC) DO<br /> FIND &#8220;saluti&#8221; %A
    </td>

    <td>
      grep &#8220;saluti&#8221; *.doc
    </td>
  </tr>

  <tr>
    <td>
      Visualizza le variabili di ambiente
    </td>

    <td>
      SET
    </td>

    <td>
      env
    </td>
  </tr>

  <tr>
    <td>
      Setta una variabile d&#8217;ambiente temporanea
    </td>

    <td>
      SET Var=Value
    </td>

    <td>
      export Var=Value
    </td>
  </tr>

  <tr>
    <td>
      Cancella una variabile d&#8217;ambiente temporanea
    </td>

    <td>
      SET Var=
    </td>

    <td>
      unset Var
    </td>
  </tr>

  <tr>
    <td>
      Elenca i driver caricati nel sistema
    </td>

    <td>
      DRIVERQUERY
    </td>

    <td>
      lsmod (non solo per i driver)
    </td>
  </tr>

  <tr>
    <td>
      Visualizza il tempo di funzionamento del sistema
    </td>

    <td>
      SYSTEMINFO
    </td>

    <td>
      uptime
    </td>
  </tr>

  <tr>
    <td>
      Visualizza lo stato della memoria RAM
    </td>

    <td>
      MEM
    </td>

    <td>
      free
    </td>
  </tr>

  <tr>
    <td>
      Schedulare processi in modo automatico.<br /> Notare che questo è un modo per far eseguire a windows processi in background
    </td>

    <td>
      schtasks<br /> at
    </td>

    <td>
      cron
    </td>
  </tr>
</table>

La lista non finisce qua, questi sono solo i comandi più importanti :-) , con la quale potete tradurre comandi per DOS in comandi per Linux, e comandi per Linux in comandi per DOS. Se sei un nuovo utente, ti consiglio la shell di Linux, molto più espressiva e personalizzabile!

Se conoscete altri comandi utili alla gestione dei sistemi, commentate pure questo articolo. CIAO!!!
