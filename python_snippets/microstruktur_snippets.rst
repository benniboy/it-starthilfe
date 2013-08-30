::
    import json
    from Products.Five import BrowserView 
    from collective.portlet.cart import readcookie, extractitems
    from collective.portlet.cart import CartDataProviderMixin
    
    class AjaxPackageData(BrowserView, CartDataProviderMixin):
               
        def __call__(self):
            items = dict(extractitems(readcookie(self.request)))        
            count = self.request.form.get('count')
            infos = [(m.get_reservable_uid(), m.Title()) 
                     for m in self.context.get_reservables()]
             
            
            results = []
            for uid, title  in infos:
                result = {}
                result["uid"] = uid
                if uid in items:
                    sumcount = count + items[uid]
                else: 
                    sumcount = count
                    
                result["validated"] = self.data_provider.validate_count(uid, 
                                                                        sumcount)
                if not result["validated"]:
                    result["title"] = title
                    
                results.append(result)
            
            return json.dumps(results)
        
        
        
          
- dict in anderes dict mit counter einbauen

::      
    info = {}
    form = self.get_form()
    
    info['search'] = form['sSearch']
    info['echo'] = form['sEcho']
    info['slicestart'] = int(form['iDisplayStart'])
    info['slicelength'] = int(form['iDisplayLength'])
    info['col_displayed'] = int(form['iColumns'])
    info['col_name'] = form['sColumns']
    info['col_regexfilter'] = form['bRegex'] == 'true'
    info['col_sortedon'] = int(form['iSortingCols'])
    
    idx = 0
    
    while 'bSortable_%d' % idx in form:
        info[idx] = {}
        info[idx]['sortable'] = form['bSortable_%d' % idx] == 'true'
        info[idx]['regex'] = form['bRegex_%d' % idx] == 'true'
        info[idx]['searchable'] = form['bSearchable_%d' % idx] == 'true'
        info[idx]['dataprop'] = form['mDataProp_%d' % idx]
        info[idx]['search'] = form['sSearch_%d' % idx]
    
        idx += 1        
        
        
        
