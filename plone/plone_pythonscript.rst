plone pythonscript
==================


 - im zmi auf site/manage: rechts oben im dropdown add script(python)

 - dann scriptl bauen
   zb:

::                                                                
    #query = {'object_provides':
    #                     {'query': ["simplelayout.base.interfaces.ISimpleLayoutBlock"],},
    #                 'sort_order': 'getObjPositionInParent'
    #                 }
    
    
    query = {'portal_type':'Blog'}
    
    for brain in context.portal_catalog(**query):
        print brain.Title, brain.getURL()
    return printed

 - die nicht auskommentierte query sucht nach portaltype Blog.
 
 
 
 - suche per UID
 
::

    query = {'UID':'1811e783bcb7040f657954af4ef3455'}
        
    for brain in context.portal_catalog(**query):
        print brain.Title, brain.getURL()
    return printed

