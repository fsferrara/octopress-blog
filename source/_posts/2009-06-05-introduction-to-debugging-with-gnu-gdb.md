---
comments: true
title: Introduction to debugging with GNU GDB
date: 2009-06-05T20:41:55+00:00
author: fsferrara
layout: post
guid: http://www.fsferrara.com/?p=56
permalink: /introduction-to-debugging-with-gnu-gdb/
categories:
  - Programming
tags:
  - c
  - debug
  - gdb
---
GNU debugger (talvolta chiamato semplicemente GDB) è il nome di un programma libero sviluppato da GNU. È il debugger predefinito del software GNU, gira su molte piattaforme (tra cui i sistemi Unix-like e Microsoft Windows) ed è capace di analizzare numerosi linguaggi di programmazione, tra cui Ada, C, C++ e Fortran.

GDB (ovvero GNU DeBugger) è molto più di un semplice debugger: è un vero e proprio program execution path analysis tool.

Invocando il comando “gdb &#8211;help” avremo:

<!--more-->

<pre class="shell">This is the GNU debugger.  Usage:

    gdb [options] [executable-file [core-file or process-id]]
    gdb [options] --args executable-file [inferior-arguments ...]

Options:

  --args             Arguments after executable-file are passed to inferior
  --[no]async        Enable (disable) asynchronous version of CLI
  -b BAUDRATE        Set serial port baud rate used for remote debugging.
  --batch            Exit after processing options.
  --cd=DIR           Change current directory to DIR.
  --command=FILE     Execute GDB commands from FILE.
  --core=COREFILE    Analyze the core dump COREFILE.
  --pid=PID          Attach to running process PID.
  --dbx              DBX compatibility mode.
  --directory=DIR    Search for source files in DIR.
  --epoch            Output information used by epoch emacs-GDB interface.
  --exec=EXECFILE    Use EXECFILE as the executable.
  --fullname         Output information used by emacs-GDB interface.
  --help             Print this message.
  --interpreter=INTERP
                     Select a specific interpreter / user interface
  --mapped           Use mapped symbol files if supported on this system.
  --nw               Do not use a window interface.
  --nx               Do not read .gdbinit file.
  --quiet            Do not print version number on startup.
  --readnow          Fully read symbol files on first access.
  --se=FILE          Use FILE as symbol file and executable file.
  --symbols=SYMFILE  Read symbols from SYMFILE.
  --tty=TTY          Use TTY for input/output by the program being debugged.
  --version          Print version information and then exit.
  -w                 Use a window interface.
  --write            Set writing into executable and core files.
  --xdb              XDB compatibility mode.</pre>

Bhè… ci sono molte opzione, come la maggior parte dei programmi :-P . in questa guida ci limiteremo a chiamare gdb passandoci semplicente il nome dell’eseguibile da analizzare.

Facciamo subito il solito primo esempio: hello.c.

<pre lang="c">#include

int main()
{
        printf("Hello World\n");
        exit(0);
}</pre>

Se vogliamo analizzare questo programma dobbiamo compilarlo con l’opzione “-g” del compilatore gcc; in questo modo l’eseguibile conterrà delle informazioni utili al debugger per analizzare il programma. Compiliamo…

<pre class="shell">emac:~/temp ferrara$ gcc -g -o helloworld hello.c
emac:~/temp ferrara$ ls -l
total 32
-rw-r--r--  1 ferrara  ferrara     72 19 Nov 22:41 hello.c
-rwxr-xr-x  1 ferrara  ferrara  11764 19 Nov 22:45 helloworld</pre>

Adesso abbiamo il nostro eseguibile chiamato “helloword” compilato per essere esaminato con gdb. Non ci resta che lanciare il comando:

<pre class="shell">emac:~/temp ferrara$ gdb helloworld
GNU gdb 5.3-20030128 (Apple version gdb-309) (Thu Dec  4 15:41:30 GMT 2003)
Copyright 2003 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "powerpc-apple-darwin".
Reading symbols for shared libraries .. done
(gdb) <strong>&lt;-- Prompt di gdb</strong></pre>

Gdb ha caricato il nostro eseguibile e ci ha presentato il suo prompt (gdb). Adesso abbiamo svariati comandi a nostra disposizione! Esaminiamo il più semplice: list. Esso, seguito dal nome della funzione o del numero di linea, ci presenta a video il sorgente:

<pre class="shell">(gdb) list main <strong>&lt; -- Comando dato al prompt di gdb</strong>
1       #include
2
3       int main()
4       {
5               printf("Hello World\n");
6               exit(0);
7       }
8</pre>

Per maggiori informazioni basta digitare il comando “help list” al prompt di gdb per avere maggiori informazioni su questo comando. Ma come fa gdb a sapere il codice del programma helloworld se noi abbiamo fassato come argomento solo l’eseguibile? Questa informazione è stata registrata nell’eseguibile grazie all’opzione –g del compilatore :-).

Ora con il comando run facciamo girare il programma all’interno di gdb:

<pre class="shell">(gdb) run &tab; &lt; -- Comando dato al prompt di gdb
Starting program: /Users/ferrara/temp/helloworld
Reading symbols for shared libraries . done
Hello World &tab; &lt;-- Output del pogramma

Program exited normally.</pre>

Come si poteva immaginare non ci sono errori. Alla fine dell’esecuzione gdb ci ripresenta il suo prompt e possiamo continuare a dargli altri comandi.

Adesso proveremo a disassemblare il codice di helloworld con il comando disass:

<pre class="shell">(gdb) disass main <strong>&lt; -- Comando dato al prompt di gdb</strong>
Dump of assembler code for function main:
0x00001da4 :    mflr    r0
0x00001da8 :    stmw    r30,-8(r1)
0x00001dac :    stw     r0,8(r1)
0x00001db0 :   stwu    r1,-80(r1)
0x00001db4 :   mr      r30,r1
0x00001db8 :   bcl-    20,4*cr7+so,0x1dbc
0x00001dbc :   mflr    r31
0x00001dc0 :   addis   r3,r31,0
0x00001dc4 :   addi    r3,r3,564
0x00001dc8 :   bl      0x1f34
0x00001dcc :   li      r3,0
0x00001dd0 :   bl      0x1dd4
End of assembler dump.</pre>

Questa funzione di gdb delizierà gli smanettoni, ma non approfondiremo questo argomento.

Per uscire dal gdb e quindi tornare al prompt della nostra shell bastera digitare il comando quit o semplicemente q.

## Primo esempio di debugging

Esaminiamo il seguente programma (segmentation_fault.c):

<pre lang="c">#include
#include

int main()
{
        char *buf;

        strcpy(buf,"HelloWorld");

        printf("%s\n", buf);

        exit(0);
}</pre>

Questo programma stampa a video “HelloWorld”. Ma eseguendolo abbiamo un errore:

<pre class="shell">emac:~/temp ferrara$ gcc -g -o sfault segmentation_fault.c
emac:~/temp ferrara$ ./sfault
Bus error</pre>

Dove abbiamo sbagliato? Lanciamo gdb e diamo il comando run per avviare il programma:

<pre class="shell">emac:~/temp ferrara$ gdb sfault <strong>&lt; -- Comando dato alla shell per avviare gdb</strong>
GNU gdb 5.3-20030128 (Apple version gdb-309) (Thu Dec  4 15:41:30 GMT 2003)
Copyright 2003 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "powerpc-apple-darwin".
Reading symbols for shared libraries .. done
(gdb) run &tab; &lt;-- Comando dato al prompt di gdb
Starting program: /Users/ferrara/temp/sfault
Reading symbols for shared libraries . done

Program received signal EXC_BAD_ACCESS, Could not access memory. <strong>&lt;-- Trovato un errore</strong>
0x90007680 in strcpy () <strong>&lt;-- La funzione dove si blocca il programma è strcpy</strong>
(gdb) <strong>&lt;-- Prompt di gdb per eventuali altri comandi</strong></pre>

Questa è un informazione utilissima, ma si può avere di più. Siccome è difficile pensare che ci sia un bug nelle glibc (cioè dove è implementata la funzione strcpy()) proviamo a pensare che abbiamo passato alla funzione i parametri sbagliati, quindi inseriremo un breakpoint alla riga 8 e mentre il programma rimane bloccato aspettando il comando step per superare il breakpoint gli faremo stampare la variabile buf e il suo contenuto per verificarlo:

<pre class="shell">(gdb) list <strong>&lt;-- Chiedo il listato del sorgente</strong>
1       #include
2       #include
3
4       int main()
5       {
6               char *buf;
7               long i;
8
9               strcpy(buf,"HelloWorld");
10
(gdb) b 8 <strong>&lt;-- Inserisco un breakpoint alla riga 8</strong>
Breakpoint 1 at 0x1d8c: file segmentatio_fault.c, line 8.
(gdb) run <strong>&lt;-- Avvio il programma</strong>
The program being debugged has been started already.
Start it from the beginning? (y or n) y <strong>&lt;-- Chiedo di ricominciare da capo</strong>
Starting program: /Users/ferrara/temp/sfault

Breakpoint 1, main () at segmentatio_fault.c:9
9               strcpy(buf,"HelloWorld"); <strong>&lt;-- Si è fermato prima di eseguire la riga 9</strong>
(gdb) p buf <strong>&lt;-- Stampo la variabile buf</strong>
$1 = 0x0
(gdb) p *buf <strong>&lt;-- Stampo il contenuto di buf</strong>
Cannot access memory at address 0x0 <strong>&lt;-- Questo è il notro errore</strong>
(gdb) bt <strong>&lt;-- Stampo lo stack del programma alla riga 8</strong>
#0  main () at segmentatio_fault.c:9
(gdb) step  <strong>&lt;-- Continuiamo l’esecuzione del programma</strong>

Program received signal EXC_BAD_ACCESS, Could not access memory.
0x90007680 in strcpy ()
(gdb) bt <strong>&lt;-- Stampo lo stack dopo il blocco del programma</strong>
#0  0x90007680 in strcpy () <strong>&lt;-- Il programma si è bloccato in questa punto</strong>
#1  0x00001d9c in main () at segmentatio_fault.c:9
(gdb) clear 8 <strong>&lt;-- Cancello il breakpoint alla riga 8</strong>
Deleted breakpoint 1
(gdb) q <strong>&lt;-- Esco da gdb perché ho tutte le informazioni che mi servono</strong>
The program is running.  Exit anyway? (y or n) y <strong>&lt;-- Confermo</strong>
emac:~/temp ferrara$ <strong>&lt;-- Prompt di shell</strong></pre>

Il codice di questo programma era molto semplice, e il bug si poteva trovare anche solo leggendo il codice sorgente. Intanto abbiamo imparato l’utilizzo base dei seguenti comandi:

<table border="0">
  <tr>
    <td>
      b
    </td>

    <td>
      (breakpoint) &#8211; Inserisce un breakpoint.
    </td>
  </tr>

  <tr>
    <td>
      step
    </td>

    <td>
      Supera il breakpoint in cui si è fermato e raggiunge il prossimo breakpoint oppure a fine del programma.
    </td>
  </tr>

  <tr>
    <td>
      clear
    </td>

    <td>
      Cancella un breakpoint.
    </td>
  </tr>

  <tr>
    <td>
      run
    </td>

    <td>
      Esegue il programma che stiamo esaminando e lo fa ripartire se si blocca o finisce.
    </td>
  </tr>

  <tr>
    <td>
      p
    </td>

    <td>
      (print) – Stampa a video il contenuto di una variabile (puntatore, struttura, o altro).
    </td>
  </tr>

  <tr>
    <td>
      bt
    </td>

    <td>
      (backtrace) – Stampa il backtrace dello stack corrente.
    </td>
  </tr>

  <tr>
    <td>
      list
    </td>

    <td>
      Stampa il codice sorgente del programma. E’ un modo per sapere in quale linea inserire il breakpoint.
    </td>
  </tr>

  <tr>
    <td>
      q
    </td>

    <td>
      (quit) – Uscita da gdb.
    </td>
  </tr>
</table>

## Programmi che richiedono parametri

Per analizzare dei programmi che richiedono parametri come questo:

<pre lang="c">#include

int main(int argc, char *argv[])
{
	int i,a;
	char *car;
	int ALLOCATO,SCRITTI;

	if (argc != 3)
		printf("usa: %s  \n",argv[0]), exit(1);

	ALLOCATO = atoi(argv[1]);
	SCRITTI = atoi(argv[2]);

	car = (char *) malloc(ALLOCATO*sizeof(char));

	for(i=0,a='a' ; i &lt; SCRITTI ; i++,a++)
		car[i]=a;

	printf("%s\n",car);

	exit(0);
}</pre>

Basta chiamare gdb come abbiamo fatto finora e passare gli argomenti assieme al comando run:

<pre class="shell">(gdb) run 5 5
Starting program: /Users/ferrara/temp/serio 5 5
Reading symbols for shared libraries . done
abcde

Program exited normally.
(gdb)</pre>

Passando come secondo argomento un numero molto grande rispetto al primo si ha un vero e proprio segmentation fault:

<pre class="shell">(gdb) run 5 99999999
Starting program: /Users/ferrara/temp/serio 5 99999999

Program received signal EXC_BAD_ACCESS, Could not access memory.
0x00001d40 in main (argc=3, argv=0xbffffce8) at serio.c:18
18                      car[i]=a;
(gdb)</pre>

Come mai accade questo? Adesso avete gli strumenti necessari per procedere da soli… buon divertimento con gdb!

## Conclusioni

Questo documento è da considerarsi una semplicissima introduzione, giusto quel che basta per cominciare ad usare il manuale di gdb senza perdersi tra le tantissime opzioni.

Per ulteriori informazioni digitare il comando “man gdb” dal prompt di shell oppure “help ” dal prompt di gdb.

Per ci si scoccia di usare un debugger a linea di comando può trovare delle front end per gdb come xxgdb.
