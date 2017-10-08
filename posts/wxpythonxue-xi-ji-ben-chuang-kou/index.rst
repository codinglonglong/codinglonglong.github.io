.. title: wxPython学习（1）——基本窗口
.. slug: wxpythonxue-xi-ji-ben-chuang-kou
.. date: 2017-10-08 18:20:07 UTC+08:00
.. tags: wxPython, Python, GUI
.. category: Python
.. link: 
.. description: 
.. type: text


基于Web的程序不方便操作本地文件，不得不回退到当初用Tkinter做界面的年代，但是Tkinter做一些复杂界面确实不容易，这回研究个相对成熟一些的桌面GUI库wxPython。前些年wxPython不支持Python3，现在支持了，可以好好学习一下了。


一个基本的wxPython窗口程序如下：

.. code-block:: python
    :number-lines:

    import wx

    class MyFrame1(wx.Frame):
    
        def __init__(self, title, parent=None, fid=-1, pos=wx.DefaultPosition, size=wx.DefaultSize):
            wx.Frame.__init__(self, parent, fid, title, pos, size)

    class App(wx.App):
        
        def OnInit(self):
            self.f =  MyFrame1(title="你好")
            self.f.Show()
            return True

    if __name__=="__main__":
        app = App()
        app.MainLoop()


运行结果：

.. image:: https://github.com/longlongpicture/myblogpicture/raw/master/wxPython1.PNG


这样就创建了一个最简单的窗口程序，在这个量级上，和Tkinter的写法非常相似。程序是App的事件循环，Frame是App的容器。后边我们将一个一个欣赏wxPython提供的窗口控件。




