socksproxy windows
==================

- putty und puttykey runterladen
- puttykey machen dann bei putty ssh key eintragen
- beim menü-> ssh -> tunnel -> dynamic 1080 port einstellen
- mit server verbindn und starten =)


ubuntu terminal
===============

- ``ssh -D 127.0.0.1:1080 user@serveradresse``

- firefox und jdownloader einrichten.
  proxy host/ip: 127.0.01 port 1080

- im ``.ssh`` ordner eine configfile machen mit:

::
    host kurzname
        HostName serveradresse
        User useradresse
        DynamicForward localhost:1080
    
- dann mit ``ssh kurzname`` schnell und praktisch über die shell verbinden
