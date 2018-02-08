.. title: Python装饰器探索
.. slug: pythonzhuang-shi-qi-tan-suo
.. date: 2017-02-01 19:31:17 UTC+08:00
.. tags: Python, decorator
.. category: Python
.. link: 
.. description: 
.. type: text

Python的装饰器是一个很有趣的语法糖，它可以让代码变得简洁优美，将与逻辑无关的部分分离出来，比如记录日志、验证权限、设置缓存、程序计时、配置上下文等等。


1、带参数函数、无参数装饰器

    .. code-block:: python
        :number-lines:

        # -*-coding:utf-8-*-
        # 带参数函数、无参数装饰器


        def checklogin(func):
            def _(username):
                validusers = ["long", "jack"]
                if username in validusers:
                    return func(username)
                else:
                    return str(username) + ", 你没有操作权限"
            return _


        @checklogin
        def login(username):
            return "欢迎你, " + str(username)


        print(login("long"))
        print(login("tom"))
        print(login("jack"))

运行结果：

    .. code-block:: bash

        欢迎你, long
        tom, 你没有操作权限
        欢迎你, jack


2、可变参数函数、无参数装饰器

    .. code-block:: python
        :number-lines:

        # -*-coding:utf-8-*-
        # 可变参数函数、无参数装饰器


        def logger(func):
            def _(*args, **kwargs):
                print(str(func.__name__) + '被调用，参数包括：' + str(args) + str(kwargs))
                if args and kwargs:
                    return func(args, kwargs)
                elif args:
                    return func(args)
                elif kwargs:
                    return func(kwargs)
                else:
                    return func()
            return _


        @logger
        def test1():
            pass


        @logger
        def test2(args):
            pass


        @logger
        def test3(kwargs):
            pass


        @logger
        def test4(args, kwargs):
            pass


        test1()
        test2("long")
        test3(a=1, b=2)
        test4("long", a=1, b=2)

运行结果：

    .. code-block:: bash

        test1被调用，参数包括：(){}
        test2被调用，参数包括：('long',){}
        test3被调用，参数包括：(){'a': 1, 'b': 2}
        test4被调用，参数包括：('long',){'a': 1, 'b': 2}


3、带参数函数、带参数装饰器

    .. code-block:: python
        :number-lines:

        # -*-coding:utf-8-*-
        # 带参数函数、带参数装饰器


        def typechecker(paramtype):
            def _outer(func):
                def _inner(*args):
                    for a in args:
                        if type(a) is not paramtype:
                            args = [str(v) for v in args]
                            return "+".join(args) + " 类型错误"
                    return func(args)
                return _inner
            return _outer


        @typechecker(int)
        def test(value):
            result = sum(value)
            value = [str(v) for v in value]
            return "+".join(value) + '=' + str(result)


        print(test(1, 2, 3, 4, 5))
        print(test(1, 2, 3, 'a', 5))

运行结果:

    .. code-block:: bash

        1+2+3+4+5=15
        1+2+3+a+5 类型错误


4、带参数函数、可变参数装饰器

    .. code-block:: python
        :number-lines:

        # -*-coding:utf-8-*-
        # 带参数函数、可变参数装饰器


        def typechecker(*paramtype):
            def _outer(func):
                def _inner(*args):
                    for a in args:
                        if type(a) not in paramtype:
                            return "参数不是有效的类型"
                    return func(args)
                return _inner
            return _outer


        @typechecker(int, str, float)
        def test(value):
            return "参数有效"


        print(test([1, 2], 5, 5.1, "a"))
        print(test(1, 2, 3, 5.2, 'a', 5))

运行结果:

    .. code-block:: bash

        参数不是有效的类型
        参数有效


5、多个装饰器的调用顺序

    .. code-block:: python
        :number-lines:

        # -*-coding:utf-8-*-
        # 多个装饰器的调用顺序


        def deco1(func):
            def _():
                print("deco1() is called.")
                return func()
            return _


        def deco2(func):
            def _():
                print("deco2() is called.")
                return func()
            return _


        @deco1
        @deco2
        def test():
            print("test() is called.")


        test()
        test()

运行结果:

    .. code-block:: bash

        deco1() is called.
        deco2() is called.
        test() is called.
        deco1() is called.
        deco2() is called.
        test() is called.

