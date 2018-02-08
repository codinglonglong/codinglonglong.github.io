.. title: Python使用装饰器实现单例模式
.. slug: pythonshi-yong-zhuang-shi-qi-shi-xian-dan-li-mo-shi
.. date: 2017-03-18 18:34:40 UTC+08:00
.. tags: Python, 设计模式, 单例模式
.. category: Python
.. link: 
.. description: 
.. type: text

    .. code-block:: python
        :number-lines:

        def singleton(cls):
            instances = {}
            def _(*args, **kw):
                if cls not in instances:
                    instances[cls] = cls(*args, **kw)
                return instances[cls]
            return _

        @singleton
        class Test():
            def __init__(self):
                self.x = 0

        t1 = Test()
        print(t1.x)
        t2 = Test()
        print(t2.x)
        t1.x = 10
        print(t1.x)
        print(t2.x)
        print(id(t1))
        print(id(t2))

运行结果：

    ::

        >> python test1.py
        0
        0
        10
        10
        45825544
        45825544

可以看到，虽然初始化两个对象，但是两个对象的id是一样的，这样就实现了单例模式。
