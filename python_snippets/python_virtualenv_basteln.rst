virutalenv
==========

local in den ordner des projectes gehn, dann

``/opt/buildout.python/bin/virtualenv-2.7 --no-site-packages --no-setuptools  .`` erzeugt mir in
./bin/python ein python interpreter mid dem ich dann abgekapselt vom systempython 
im projekt rumvurwerken kann evtl mit ``--clear``

bei plonesachen
dann entweder
``./bin/python bootstrap.py -c dev.cfg``

oder

``./bin/python bootstrap.py -v 1.6 -c dev.cfg``



sonsch bei nonplone buildout 2.0 und dann mit ohne -v version rennen lassen
rennen lassen und ./bin/buildout script ist erstellt


``./bin/buildout -c dev.cfg``




