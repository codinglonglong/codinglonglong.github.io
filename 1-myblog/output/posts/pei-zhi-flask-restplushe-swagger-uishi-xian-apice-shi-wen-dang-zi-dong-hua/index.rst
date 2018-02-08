.. title: 配置Flask-Restplus和Swagger UI实现API测试文档自动化
.. slug: pei-zhi-flask-restplushe-swagger-uishi-xian-apice-shi-wen-dang-zi-dong-hua
.. date: 2017-01-24 13:21:42 UTC+08:00
.. tags: Python, flask-restplus, swagger ui
.. category: Python
.. link: 
.. description: 
.. type: text

继文章 https://codinglonglong.github.io/posts/dockerpei-zhi-kai-fa-jing-xiang/ 之后，我们继续实验。

1、Docker中安装Flask-Restplus。

        .. code-block:: bash

            pip install flask-restplus

2、主系统编写测试程序main.py。

        .. code-block:: python
            :number-lines:

            from flask import Flask
            from flask_restplus import Api, Resource, fields

            app = Flask(__name__)
            api = Api(app, version='1.0', title='Sample API',
                description='A sample API',
            )

            @api.route('/my-resource/<id>')
            @api.doc(params={'id': 'An ID'})
            class MyResource(Resource):
                def get(self, id):
                    return {}

                @api.response(403, 'Not Authorized')
                def post(self, id):
                    api.abort(403)


            if __name__ == '__main__':
                app.run(debug=True, host="0.0.0.0", port=8080)
                
3、Docker中运行程序。

        .. code-block:: bash

            cd /usr/development/
            python main.py

4、主系统查看测试结果。

.. image:: https://github.com/longlongpicture/myblogpicture/raw/master/flaskswaggerui.PNG


可以看到通过Swagger UI，我们能够很方便地在浏览器上测试API的可用性。
