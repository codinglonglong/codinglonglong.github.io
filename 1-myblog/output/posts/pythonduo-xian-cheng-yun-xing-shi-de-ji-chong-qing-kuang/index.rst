.. title: Python多线程运行时的几种情况
.. slug: pythonduo-xian-cheng-yun-xing-shi-de-ji-chong-qing-kuang
.. date: 2015-09-09 10:41:07 UTC+08:00
.. tags: Python, 多线程
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text


本文学习Python在多线程运行时的几种情况。

看代码，这是一个标准的多线程程序：

.. code-block :: python
    :linenos:

    import time
    start = time.clock()

    import threading


    class Stu:

        def __init__(self, name):
            self.name = name

        def __str__(self):
            return self.name

        def run(self):
            time.sleep(2)
            with open("datas", "a") as fp:
                fp.writelines("puts " + str(self.name) + "\n")


    def spawn(target, *args, **kw):
        t = threading.Thread(
            target=target, name=target.__name__, args=args, kwargs=kw)
        t.start()
        return t

    with open("datas", "a") as fp:
        fp.writelines("main thread start.\n")
    studentlist = ['a', 'b', 'c', 'd', 'e']
    [spawn(Stu(x).run) for x in studentlist]
    with open("datas", "a") as fp:
        fp.writelines("main thread end here.\n")

    end = time.clock()
    print(end - start)
    
我们来看程序的输出：
    
::

   >> long@happytime:~/envtest$ python envtester.py 
   >> 0.005009
   >> long@happytime:~/envtest$ cat datas 
   >> main thread start.
   >> main thread end here.
   >> puts c
   >> puts a
   >> puts d
   >> puts b
   >> puts e


线程都正常启动了，主线程最先结束，然后每个线程分别向datas中写入自己的name。这是最简单的多线程，也是没有任何控制的多线程。

下一步，我们如果设置守护线程，看看会发生什么。

.. code-block :: python
    :linenos:

    import time
    start = time.clock()

    import threading


    class Stu:

        def __init__(self, name):
            self.name = name

        def __str__(self):
            return self.name

        def run(self):
            time.sleep(2)
            with open("datas", "a") as fp:
                fp.writelines("puts " + str(self.name) + "\n")


    def spawn(target, *args, **kw):
        t = threading.Thread(
            target=target, name=target.__name__, args=args, kwargs=kw)
        t.daemon = True
        t.start()
        return t

    with open("datas", "a") as fp:
        fp.writelines("main thread start.\n")
    studentlist = ['a', 'b', 'c', 'd', 'e']
    [spawn(Stu(x).run) for x in studentlist]
    with open("datas", "a") as fp:
        fp.writelines("main thread end here.\n")

    end = time.clock()
    print(end - start)

运行结果：

::

   >> long@happytime:~/envtest$ python envtester.py 
   >> 0.005924
   >> long@happytime:~/envtest$ cat datas 
   >> main thread start.
   >> main thread end here.

我们发现，一旦将子线程设置为daemon，也就是守护线程，主线程结束后，程序就退出了，子线程也结束了。要注意的地方是，daemon要在start之前调用。

那如果我们想让子线程都结束后，主线程再继续执行，该如何实现呢？看代码：

.. code-block :: python
    :linenos:

    import time
    start = time.clock()

    import threading


    class Stu:

        def __init__(self, name):
            self.name = name

        def __str__(self):
            return self.name

        def run(self):
            time.sleep(2)
            with open("datas", "a") as fp:
                fp.writelines("puts " + str(self.name) + "\n")


    def spawn(target, *args, **kw):
        t = threading.Thread(
            target=target, name=target.__name__, args=args, kwargs=kw)
        t.start()
        t.join()
        return t

    with open("datas", "a") as fp:
        fp.writelines("main thread start.\n")
    studentlist = ['a', 'b', 'c', 'd', 'e']
    [spawn(Stu(x).run) for x in studentlist]
    with open("datas", "a") as fp:
        fp.writelines("main thread end here.\n")

    end = time.clock()
    print(end - start)

程序运行结果：
::

   >> long@happytime:~/envtest$ python envtester.py 
   >> 0.007657
   >> long@happytime:~/envtest$ cat datas 
   >> main thread start.
   >> puts a
   >> puts b
   >> puts c
   >> puts d
   >> puts e
   >> main thread end here.

从结果可以明显看出，尽管子线程都需要花费时间执行，但主线程最后结束。

综上，如果想让：

1） 主线程和子线程混乱执行，使用默认的多线程即可；

2） 主线程结束后，子线程不管有没有执行完都结束，使用守护线程的方法；

3） 主线程等待子线程结束，使用join方法。  

