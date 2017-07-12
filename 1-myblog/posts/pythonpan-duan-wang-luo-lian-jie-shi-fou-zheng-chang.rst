.. title: Python判断网络连接是否正常
.. slug: pythonpan-duan-wang-luo-lian-jie-shi-fou-zheng-chang
.. date: 2017-07-12 21:25:51 UTC+08:00
.. tags: Python
.. category: Python
.. link: 
.. description: 
.. type: text

.. code-block:: python
    :number-lines:

    def checkconnection():
        proxies = {"http": "http://192.168.1.254:8228", "https": "http://192.168.1.254:8228"}
        try:
            r1 = requests.get("http://www.facebook.com",
                              proxies=proxies,
                              timeout=5)
            if str(r1.status_code) == "200":
                return True
            return False
        except Exception as e:
            return False


**注意**

如果不需要测试代理，去掉 **proxies=proxies，** 就可以了。

