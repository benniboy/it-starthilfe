shell snippets
==============

- mit ``tree ordnername`` kann mann ordnerstruktur anschauen

- ``cat ordnername`` ist ausgeben

- ``less ordnername`` ist wie cat, nur das es auch scrollbar ist
- mit ``head`` filestart
- mit ``tail`` fileende anschauen
- mit ``tail -f filename`` (follow, heißt automatisch neue zeilen anzeigen)


- mit ``vi filename`` kann man files anschauen und bearbeiten.
- mit ``i`` in insert mode gehen
- mit ``escape`` aus dem insert mode gehen
- mit ``:wq`` write und quit
- mit ``dd`` ganze zeile löschen und gleichzeitig in den puffer legen
- mit ``10dd`` zb. 10 zeilen löschen und dann woanders mit p einfügen

- ``p`` (paste)

- ``x`` is copyline (kopieren und woanders einfügen

- ``a`` ist append am ende der zeile


prozess suchen =)
=================
::

    ps waux |grep "suchname

grep
====

- in ordner gehen dann mit recursive, zeilennummeranzeige und I ist keine
   binärdaten durchsuchen dann suchbegriff und dateiendung. * = alles
::
    grep -rnI layoutmanager *

- wenn man etwas finden will, mit . in den aktueller ordner dann
   -name suchstring blabla.* oder .dateiendung
::
    find . -name credentials.dat

- ``sudo update-alternatives --config editor`` da kann man sich
    die default anwendungen via viele ubuntu-sachen auswählen.



header einer website via consolenbefehl auslesen

Here is an example showing how to test loading the page using the wget UNIX
command-line utility (discard the retrieved document and print the HTTP response headers):

::

    $ wget --output-document=/dev/null --server-response http://localhost:8080/
    
   
- pgrep mit suchwert
 
::
    pgrep python  
        
tar machen    
==========

- Connect to a shell or open a terminal/console on your Linux/Unix machine.

  To create an archive of a directory and its contents you would type the following and press enter:
  tar -cvf name.tar /path/to/directory

  Substitute the name.tar with the name of the tar file you would like to create and substitute the 
  directory name for the full path to the directory you would like to archive.
  To create an archive of certfain files you would type the following and press enter:
  tar -cvf name.tar /path/to/file1 /path/to/file2 /path/to/file3

  Substitute the name.tar with the name of the tar file you would like to create 
  and substitute the the various files for the full path to the files you would 
  like to archive. Each file you would like included in the archive should
  be seperated by a space.    
    


extract tar and install
=======================

download tar::

extract::
    tar zxf /pathtofio.tar

cd to extracted then ::
    ./configure
    make
    sudo make install
    
