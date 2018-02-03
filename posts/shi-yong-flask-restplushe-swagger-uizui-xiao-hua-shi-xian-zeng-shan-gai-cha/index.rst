.. title: 使用Flask-Restplus和Swagger UI最小化实现增删改查
.. slug: shi-yong-flask-restplushe-swagger-uizui-xiao-hua-shi-xian-zeng-shan-gai-cha
.. date: 2017-01-24 17:13:27 UTC+08:00
.. tags: Python, flask-restplus, swagger ui
.. category: Python
.. link: 
.. description: 
.. type: text

继文章 https://codinglonglong.github.io/posts/pei-zhi-flask-restplushe-swagger-uishi-xian-apice-shi-wen-dang-zi-dong-hua/ 之后，我们参考文档实现了一个最小化增删改查的案例。

        .. code-block:: python
            :number-lines:

            #-*-coding:utf-8-*-
            from flask import Flask
            from flask.ext.restplus import Api, Resource, fields

            app = Flask(__name__)
            api = Api(app, version='1.0', title='TodoMVC API',
                    description='A simple TodoMVC API',
                    )

            ns = api.namespace('todos', description='TODO operations')

            todo = api.model('Todo', {
                'id': fields.Integer(readOnly=True, description='The task unique identifier'),
                'task': fields.String(required=True, description='The task details')
            })


            class TodoDAO(object):

                def __init__(self):
                    self.counter = 0
                    self.todos = []

                def get(self, id):
                    for todo in self.todos:
                        if todo['id'] == id:
                            return todo
                    api.abort(404, "Todo {} doesn't exist".format(id))

                def create(self, data):
                    todo = data
                    todo['id'] = self.counter = self.counter + 1
                    self.todos.append(todo)
                    return todo

                def update(self, id, data):
                    todo = self.get(id)
                    todo.update(data)
                    return todo

                def delete(self, id):
                    todo = self.get(id)
                    self.todos.remove(todo)


            DAO = TodoDAO()
            DAO.create({'task': 'Build an API'})
            DAO.create({'task': '你好'})


            @ns.route('/')
            class TodoList(Resource):
                '''Shows a list of all todos, and lets you POST to add new tasks'''

                def get(self):
                    '''List all tasks'''
                    return DAO.todos

                @ns.expect(todo)
                def post(self):
                    '''Create a new task'''
                    return DAO.create(api.payload), 201


            @ns.route('/<int:id>')
            @ns.response(404, 'Todo not found')
            @ns.param('id', '任务标识')
            class Todo(Resource):
                '''Show a single todo item and lets you delete them'''

                def get(self, id):
                    '''Fetch a given resource'''
                    return DAO.get(id)

                def delete(self, id):
                    '''Delete a task given its identifier'''
                    DAO.delete(id)
                    return '', 204

                @ns.expect(todo)
                def put(self, id):
                    '''Update a task given its identifier'''
                    return DAO.update(id, api.payload)


            if __name__ == '__main__':
                app.run(debug=True, host="0.0.0.0", port=8080)

运行结果：

.. image:: https://github.com/longlongpicture/myblogpicture/raw/master/flaskswageruifull.PNG

在这个例子中，我们实现了五种最基本的API：

1. 查询全部todo
2. 添加todo
3. 查询某一个todo
4. 删除某一个todo
5. 更新某一个todo

而更复杂的项目都是基于这五种API展开的，从这里我们也可以看出RESTful Web Services的技术美感， **simple is better** 。

