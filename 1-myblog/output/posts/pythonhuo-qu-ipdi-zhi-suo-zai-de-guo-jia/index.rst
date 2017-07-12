.. title: Python获取IP地址所在的国家
.. slug: pythonhuo-qu-ipdi-zhi-suo-zai-de-guo-jia
.. date: 2017-07-12 19:41:18 UTC+08:00
.. tags: Python
.. category: Python 
.. link: 
.. description: 
.. type: text

.. code-block:: python
    :number-lines:
    
    import simplejson

    def getipposition(ipstr):
        r = requests.post("http://int.dpool.sina.com.cn/iplookup/iplookup.php?format=json&ip="+ipstr,
                          timeout=10)
        return simplejson.loads(r.text)["country"]