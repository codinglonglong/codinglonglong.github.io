.. title: TypeError: Decimal('5') is not JSON serializable
.. slug: typeerror-decimal5-is-not-json-serializable
.. date: 2017-02-01 13:18:57 UTC+08:00
.. tags: flask, jsonify
.. category: Python
.. link: 
.. description: 
.. type: text

在使用Flask的jsonify时，返回Decimal对象会出现标题中的错误。通过如下方法可以解决：

    .. code-block:: bash

        pip install simplejson

