- zuerst leeres set anlegen und mit update list comp wird dann jedes nur 1 mal
  ins set aufgenommen. (wert ist immer nur 1 mal im set)

::      
    usedcriterias = set()
    
    for brain in results:
        criterias = obj.listCriteria()
        usedcriterias.update([_.__class__ for _ in criterias])
        
        (das obrige ist wie die kurzform einer for schleife=)
                  
    pprint(usedcriterias)

- _.(irgnd eine methode etc aufrufen)  for _ in blabla
  gleichzeiteiges setzen von key: value

::

    {_:_ * _ for _ in range(20)}
    
- ausgabe ist:
  {0: 0, 1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64, 9: 81, 10: 100,
  11: 121, 12: 144, 13: 169, 14: 196, 15: 225, 16: 256, 17: 289, 18: 324, 19: 361}
