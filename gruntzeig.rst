scheiß node grafl-.-



wget http://nodejs.org/dist/node-latest.tar.gz
tar -xzvf node-latest.tar.gz
cd node-v0.10.29

./configure
 make
 sudo make install


dann des machen:

http://stackoverflow.com/questions/22269101/grunt-dependencies-conflicts-in-bootstrap
I ran into this problem this morning too. I ended up changing line 30 in Bootstrap's package.json file: from "~0.4.2" to "0.4.2":
27  "devDependencies": {
...
30    "grunt" : "0.4.2"
This means that 0.4.3 no longer matches the dependency spec but it also means you won't install new versions of grunt later. It's enough to get things working but you should probably change it back eventually (maybe in your next bootstrap project leave it alone).



sudo /usr/local/bin/npm install   im bootstrap root ordner. evtl spata symlinks


