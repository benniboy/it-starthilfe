In the following tutorial i´ll try to explain how to create a python egg with
a script and a self contained buildout.

we will make a simple example egg and then set it up on pypi so that later
all you have to is to download it and let the magic happen=)

move to your workspace folder and create a new folder and name it
like your desired eggname.

inside your folder, you paste the bootstrap.py so that later the buildout
can be made

create a new file named buildout.cfg in your folder

open your new buildout.cfg and write something like that.
this is just a simple buildout.cfg for more information google python buildout

::
    [buildout]
    parts = 
        myfancyexample
    
    unzip = true
    develop = .
    
    [checkclientdisconnected]
    recipe = 
        zc.recipe.egg:script
    eggs =
        my.fancy.example

the next thing we will create is the setup.py which contains information
and some metadata of our egg.

::
    from setuptools import setup, find_packages
    import sys, os
    
    version = '1.0beta'
    shortdesc = 'checks and restarts plone 3 zeo-clients if disconnected'
    longdesc = " "
    longdesc =  open(os.path.join(os.path.dirname(__file__), 'README.rst')).read()  
    longdesc += open(os.path.join(os.path.dirname(__file__), 'HISTORY.rst')).read()  
    longdesc += open(os.path.join(os.path.dirname(__file__), 'LICENSE.rst')).read()  


:: 
    setup(name='my.fancy.example',
          version=version,
          description=shortdesc,
          long_description=longdesc,
          classifiers=[
                'Development Status :: 4 - Beta',
                'License :: OSI Approved :: BSD-simplified',
                'Operating System :: OS Independent',
                'Programming Language :: Python', 
                'Topic :: Software Development',
                "Framework :: Plone",
          ],
          keywords='',
          author='your name',
          author_email='yourname@example.com',
          url=u'eventually add a repository location here',
          license='BSD-simplified',
          packages=find_packages('src'),
          package_dir = {'': 'src'},
          namespace_packages=["my", "my.fancy"],
          include_package_data=True,
          zip_safe=False,
          install_requires=[
                'setuptools',   
          ],
    
          entry_points={
          'console_scripts': ['myfancyexamplescript = my.fancy.example:run'],
          },
    )

now in your folder create another folder named src

inside this new folder the nested namespace comes to effect. in our example
the my.fancy.example. each word before the dot is a namespace and now we create
the folderstructure like that.

inside the src folder create now a folder named my

in the my folder create a __init__.py file and put the following code in it:
__import__('pkg_resources').declare_namespace(__name__)

each nested namespace folder needs to have such a file so that the eggbuilding
process we need later will work.

now inside the my folder create a new named folder named fancy and again put
a ``__init__.py`` with the code:
``__import__('pkg_resources').declare_namespace(__name__)`` in it.

again make a new folder inside the fancy folder named example.
switch to that newly created folder.

Usually all of your sourcecode needed and used by your python egg will come here.
In our example a simple script.

create a new file named myfancyexamplescript.py it should contain the
following lines of code:

::
    import subprocess
    
    def run():
        exampleoutput = subprocess.Popen(["ls", "-la"])
        exampleoutput()

this little piece off code will run the ``ls -la``
command when you execute the myfancyexamplescript.




so now lets check if we have done everything correctly till now.
   open a terminal and move to the base-folder of our example

   ----example----

    ``$ cd ~/user/workspace/myfancyexample``

we need to run the bootstrap.py now with a python interpreter.

  ----example----

  ``$ python2.6 bootstrap.py``

  After a short time something like "created script" should be on your screen

the next step is to run the buildout. on your terminalscreen you should
still be in ``~/user/workspace/myfancyexample``
Now run ``$ ./bin/buildout``

when buildout is finished you can finally run the examplescript
``$ ./bin/myfancyexamplescript``

If everything went as we wanted, you created your first own script=) Gratz!

The next usuall step to create a python egg is to add 4 files:

a README.rst in which you descripe what your egg does
a HISTORY.rst which describes the history and for example the updates etc of your egg
a LICENSE.rst to describe on which License your egg should be
and finally a MANIFEST.in which is needed for the egg creation.
it should contain the following code:

::
    include *.rst
    recursive-include src *
    recursive-exclude src *.pyc *.pyo

to finally create the egg run the following

  ``python setup.py sdist``
  ``python setup.py sdist register upload``
  ``python setup.py sdist upload``
now your egg is ready. An usual method is to put it on version controll now.
Good options are git or svn.

