In the following tutorial i´ll try to explain how to create a plone addon with a self contained buildout.

we will make a simple example addon which is quite similar to creating a python egg.


1. move to your workspace folder and create a new folder and name it like your desired addonname.

2. inside your folder, you paste the bootstrap.py so that later the buildout can be made

3. create a new file named buildout.cfg in your folder

4. open your new buildout.cfg and write something like that.
   this is jsut a simple buildout.cfg for more information google python buildout=)

----example----

[buildout]

find-links +=
http://effbot.org/downloads/
parts = instance
extends = http://dist.plone.org/release/4.2-latest/versions.cfg
unzip = true
develop = .

[instance]
recipe = plone.recipe.zope2instance
http-address = 8080
user = admin:admin
eggs =

myfancy.addon

zcml =
myfancy.addon




5. the next thing we will create is the setup.py which contains information and some metadata of our addon.

from setuptools import setup, find_packages
import sys, os

version = '1.2'
shortdesc = 'What my fancy addon does'
longdesc = open(os.path.join(os.path.dirname(__file__), 'README.rst')).read()
longdesc += open(os.path.join(os.path.dirname(__file__), 'HISTORY.rst')).read()
longdesc += open(os.path.join(os.path.dirname(__file__), 'LICENSE.rst')).read()

setup(name='myfancy.addon',
      version=version,
      description=shortdesc,
      long_description=longdesc,
      classifiers=[
            'Development Status :: 4 - Beta',
            'License :: OSI Approved :: GNU General Public License (GPL)',
            'Operating System :: OS Independent',
            'Programming Language :: Python',
            'Topic :: Software Development',
            "Framework :: Plone",
      ],
      keywords='',
      author='your name',
      author_email='yourname@example.com',
      url=u'eventually add a repository location here',
      license='GPLv2',
      packages=find_packages('src'),
      package_dir = {'': 'src'},
      namespace_packages=[],
      include_package_data=True,
      zip_safe=True,
      install_requires=[
            'setuptools',
            'Plone',
            'myfancy.addon',
      ],
      entry_points="""
[z3c.autoinclude.plugin]
target = plone
""",
)


6. now in your folder create another folder named src
7.inside this new folder the nested namespace comes to effect. in our example the my.fancy.example
each word before the dot is a namespace and now we create the folderstructure like that.

inside the src folder create now a folder named myfancyand inside a folder named addon

8.in each namespace folder create a __init__.py file and put the following code in it:
__import__('pkg_resources').declare_namespace(__name__)

each nested namespace folder needs to have such a file so that the eggbuilding process we need later will work.

9. now inside the my folder create a new named folder addon and again put a __init__.py with the code: __import__('pkg_resources').declare_namespace(__name__)   in it.




11. Usually all of your sourcecode, data, configfiles etc needed by your addon will come here. 
    In our example a simple script.


12.create a new file named myfancyexamplescript.py it should contain the following lines of code:








13.so now lets check if we have done everything correctly till now.
   open a terminal and move to the base-folder of our example

   ----example----

    $ cd ~/user/workspace/myfancyexample

14. we need to run the bootstrap.py now with a python interpreter.

  ----example----

  $ python2.7 bootstrap.py

  After a short time something like "created script" should be on your screen

15. the next step is to run the buildout. on your terminalscreen you should still be in ~/user/workspace/myfancyexample. Now run:

  ----example----
  $ ./bin/buildout

16.  when buildout is finished you can finally run 

  ----example----
  $ ./bin/instance fg

  If everything went as we wanted, your zope should be starting and you can visit the plone site Gratz!

17. The next usuall step to create an addon is to add 4 files:
  
  a README.rst in which you descripe what your egg does
  a HISTORY.rst which describes the history and for example the updates etc of your egg
  a LICENSE.rst to describe on which License your egg should be
  and finally a MANIFEST.in which is needed for the egg creation. it should contain the following code:
 
 
  ----example----

  include *.rst
  recursive-include src *
  recursive-exclude src *.pyc *.pyo

18. to finally create te egg run the following 

  ----example----

  $ python setup.py bdist_egg



  -.....



19. now your egg is ready. An usual method is to put it on version controll now. Good options are git or svn.



















