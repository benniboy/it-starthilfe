::

    [buildout]
    find-links +=
        http://effbot.org/downloads/
    parts = instance omelette
    extends = http://dist.plone.org/release/4.3-latest/versions.cfg
    unzip = true
    develop = .
    extensions = buildout.eggscleaner
     
    [instance]
    recipe = plone.recipe.zope2instance
    http-address = 8080
    user = admin:admin
    environment-vars =
        zope_i18n_compile_mo_files true
     
    eggs =
        Pillow
        plone.reload
        plone.app.debugtoolbar
     
    zcml =
        plone.reload
     
    [omelette]
    recipe = collective.recipe.omelette
    eggs = ${instance:eggs}

