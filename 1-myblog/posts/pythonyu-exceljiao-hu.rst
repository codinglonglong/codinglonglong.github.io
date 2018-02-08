.. title: Python与Excel交互
.. slug: pythonyu-exceljiao-hu
.. date: 2018-02-08 10:31:31 UTC+08:00
.. tags: Python, Excel, xlwings
.. category: Python
.. link: 
.. description: 
.. type: text


1、安装xlwings，参考 http://docs.xlwings.org/en/stable/installation.html#installation。

2、创建项目。

    ::

        >> xlwings quickstart myproject

    生成了两个文件。
    
    .. image:: https://github.com/longlongpicture/myblogpicture/raw/master/exceljiaohu1.PNG

    其中，myproject.xlsm是Excel文件，myproject.py用来写一些功能函数。

3、打开myproject.py，编写工具。

    .. code-block :: python
        :linenos:

        import xlwings


        def addlist():
            wb = xlwings.Book.caller()
            wb.sheets[0].range("A1").value = [(1,),(2,),(3,),(4,),(5,)]
            wb.sheets[0].range("B2").value = [6,7,8,9,10]


        @xlwings.func
        def sumlist(ls):
            return sum(ls)

4、打开myproject.xlsm，提示“宏已被禁用”，点击"启用内容"按钮。

5、按下 Alt+F11，启动Microsoft Visual Basic for Applications，双击"Sheet1"。


    .. code-block :: basic
        :linenos:

        Sub HelloWorld()
            RunPython ("import myproject; myproject.addlist()")
        End Sub

6、点击工具栏上的绿色三角按钮，执行代码。

    .. image:: https://github.com/longlongpicture/myblogpicture/raw/master/exceljiaohu2.PNG

7、测试xlwings选项卡，设置Interpreter（Python解释器）、PYTHONPATH（Python模块路径）、UDF Modules（用户定义函数），点击Import Functions，弹出命令行窗口，最小化不要关闭。

    .. image:: https://github.com/longlongpicture/myblogpicture/raw/master/exceljiaohu3.PNG

8、在Excel中编写公式。

    .. image:: https://github.com/longlongpicture/myblogpicture/raw/master/exceljiaohu4.PNG

9、回车可以看到运算结果。

    .. image:: https://github.com/longlongpicture/myblogpicture/raw/master/exceljiaohu5.PNG

通过同样的原理，我们可以用Python完成Excel中需要编写VBA才能完成的事情，尤其结合Python强大的数据分析能力和Excel强大的数据组织能力，可以非常有力地提高数据分析的效率。

