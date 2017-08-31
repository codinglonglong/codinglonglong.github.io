.. title: Flask-CORS解决Ajax跨域请求问题
.. slug: flask-corsjie-jue-ajaxkua-yu-qing-qiu-wen-ti
.. date: 2017-02-08 12:59:14 UTC+08:00
.. tags: Flask-CORS, Ajax
.. category: Python
.. link: 
.. description: 
.. type: text

在本地开发网站的过程中，js访问后端服务会出现

.. code-block:: bash

    已拦截跨源请求：同源策略禁止读取位于 http://192.168.99.100:8080/signup/ 的远程资源。（原因：CORS 头缺少 'Access-Control-Allow-Origin'）。

这时可以通过Flask-CORS解决问题。

1、安装。

    .. code-block:: bash

        pip install flask-cors

2、使用。

    .. code-block:: python
        :number-lines:

        from flask_cors import CORS
        global_app = Flask(__name__)
        CORS(global_app)

