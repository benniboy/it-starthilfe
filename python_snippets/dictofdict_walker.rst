def devicelist(root_path='/sys/bus/usb/devices'):
    res = []
    def walk(parent):     
        for child in parent.values():
            res.append(child)
            walk(child)
    walk(usb_roots(root_path=root_path))
    return res
