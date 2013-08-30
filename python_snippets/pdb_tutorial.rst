Useful pdb commands
===================

- Just type the command and hit enter.

- ``l`` too see where i am in the code

- ``s`` step into, go into the function in the cursor

- ``n`` step over, execute the function under the cursor without stepping into it

- ``c`` continue, resume program

- ``w`` where am I? displays current location in stack trace

- ``b`` set breakpoint

- ``cl`` clear breakpoint

- ``bt`` print stack trace

- ``up`` go to the scope of the caller function

- ``p`` prints the variable,object...

- ``pp`` pretty print object

- ``until`` Continue execution until the line with the line number greater
  than the current one is reached or when returning from current frame
  The until command (or unt) is available only on Plone 4.x or superior as it
  is a new feature provided by the pdb module under Python 2.6.

Useful pdb snippets
===================
- Output object's class: ``print obj.__class__``

- Output object attributes and methods: ``for i in dir(obj): print i``

- Print local variables in the current function: ``print locals()``

- Dumping incoming HTTP GET or HTTP POST:
  ``print "Got request:"``
  ``for i in self.request.form.items(): print i``

- Executing code on the context of the current stack frame:
  ``pp my_tags``
  ``['bar', 'barbar']``

  ``!my_tags = ['foo', 'foobar']``
  ``pp my_tags``
  ``['foo', 'foobar']``

- Note
  The example above will modify the previous value of the variable my_tags
  in the current stack frame.

