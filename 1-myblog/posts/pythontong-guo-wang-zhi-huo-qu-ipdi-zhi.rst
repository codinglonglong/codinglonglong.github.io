.. title: Python通过网址获取IP地址
.. slug: pythontong-guo-wang-zhi-huo-qu-ipdi-zhi
.. date: 2017-07-12 19:39:51 UTC+08:00
.. tags: Python
.. category: Python 
.. link: 
.. description: 
.. type: text

.. code-block:: python
    :number-lines:

    def getipbyhost(hostaddress):
        ip = socket.gethostbyname(hostaddress)
        return ip

        