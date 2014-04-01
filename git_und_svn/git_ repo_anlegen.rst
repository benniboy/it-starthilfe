via console
===========


global git config editieren
---------------------------

vim .git/config



local in ordner des projektes gehen

dann: ``git init``

- evtl im rootordner ein .gitignore file anlegen um gewisse sachen auszulassen.
   dieses .gitignore natürlich via git add hinzufügen.

- bsp für ein .gitignorefile:

::

    *.pyc
    /bin
    /devsrc/
    /parts/
    /var/
    /src/
    *.egg-info/
    .mrsd
    /eggs/
    /develop-eggs/
    .*.cfg
    /coverage/
    /.project
    /.pydevproject
    /.settings/


- dann: ``git remote add github git@github.com:kontoname/repositoryname.git``


- fürs plone collective
  git@github.com:collective/collective.customicons.git


- mit git remote -v
  sich i di pfade wos am git gspeichert wird
  
- dann mit ``git push -u origin master`` pushen
  
  
  
  
- Create a new repository on the command line
::
    git init
    git add README.md
    git commit -m "first commit"
    git remote add origin git@github.com:benniboy/it-starthilfe.git
    git push -u origin master
  
- git origin ändern  
  If you created your repo copy by “clone” operation you will have “origin” remote 
  branch defined. This remote can be used to pull/push changes.

  ``git remote -v``

  If you decide to change this definition later you can issue the following commands:
::
  git remote rm origin
  git remote add origin git@github.com:aplikacjainfo/proj1.git
  git config master.remote origin
  git config master.merge refs/heads/master

  After this change you can push your commits to new repository location 
  (origin is selected as default remote branch for master, it’s configured in .git/config):

  ``git push``
  or ````git push origin master``








password cachen
git config --global credential.helper 'cache --timeout=3600'







git tagging
-----------
miezekatze@bennybunny:~/workspace/collective.customicons$ git tag 1.1
miezekatze@bennybunny:~/workspace/collective.customicons$ git push --tags
Total 0 (delta 0), reused 0 (delta 0)
To git@github.com:collective/collective.customicons.git
 * [new tag]         1.1 -> 1.1
miezekatze@bennybunny:~/workspace/collective.customicons$ 





 - wenn was von git auf lokale maschine speichern:
   in den workspace gehen und dann:
   ``git clone gitadressevomprojekt`` (am besten ssh adresse)







git branches und so
-------------------

des hohlt mir alle branches
git fetch --all

clone specific branch of a project
git clone -b my-branch git@github.com:plone/Products.CMFPlone.git

