secure copy
===========

- mit secure copy kann man files von der lokalen maschine auf den server spielen.
  (und umgekehrt)

- von lokal auf server 
  scp dann filename(pfad) dann benutzername@server:verzeichnis/pfad/filenameamserver

  beispiel:
  ``scp mysound.mp4 johndoe@myserver:testfolder/``

   
- von server auf lokal
  (nicht in der shell am server sondern von lokaler shell aus machen

  beispiel:
  scp user@server:/pfad/filename.endung wohinlegen/auf/lokalenrechner/
