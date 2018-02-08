.. title: Python构造对象编号自动加一
.. slug: pythongou-zao-dui-xiang-bian-hao-zi-dong-jia-yi
.. date: 2015-09-08 10:46:21 UTC+08:00
.. tags: Python, classmethod
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

   这是一个Python中类方法的使用案例。

我们如何实现每生成一个对象，它的编号就自动加1呢？

看代码：

.. code-block :: python
    :linenos:

    class Stu:

        def __init__(self):
            self.id = self.getnewid()
            self.name = "写程序的龙龙"
            self.url = "https://codinglonglong.github.io"

        def __str__(self):
            return "id: " + str(self.newid) + "\n" + \
                "name: " + str(self.name) + "\n" + \
                "blog: " + str(self.url)

        newid = 0  

        @classmethod
        def getnewid(cls):
            cls.newid = cls.newid + 1
            return cls.newid


    stu1 = Stu()
    print(stu1)
    print("*" * 50)
    stu2 = Stu()
    print(stu2)


运行程序，得到如下结果：
::

   >> long@mylife:~$ python3 test.py 
   >> id: 1
   >> name: 写程序的龙龙
   >> blog: https://codinglonglong.github.io
   >> **************************************************
   >> id: 2
   >> name: 写程序的龙龙
   >> blog: https://codinglonglong.github.io


我们看到，每初始化一个对象，对象的id就增加了1。
