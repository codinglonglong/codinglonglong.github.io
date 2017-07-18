.. title: Python通过配置文件动态修改全局变量
.. slug: pythontong-guo-pei-zhi-wen-jian-dong-tai-xiu-gai-quan-ju-bian-liang
.. date: 2015-09-09 10:06:20 UTC+08:00
.. tags: Python, exec
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text


本文学习如何通过配置文件动态修改全局变量。

看代码main.py：

.. code-block :: python
    :linenos:

    import conf
    print(conf.defaultpath)
    conf.load_conf()
    print("*" * 50)
    print(conf.defaultpath)

和代码conf.py：

.. code-block :: python
    :linenos:

    defaultpath = "/home/long/"


    def load_conf():
        data = "defaultpath = '/home/long/test'"
        exec data in globals(), globals()

运行结果：
::

   >> long@happytime:~/exectest$ python main.py 
   >> /home/long/
   >> **************************************************
   >> /home/long/test

通过load_conf()函数，我们的程序动态修改了全局变量。通过这样的方式就可以实现初始按照默认配置、必要时通过配置文件对全局变量进行修改了。
