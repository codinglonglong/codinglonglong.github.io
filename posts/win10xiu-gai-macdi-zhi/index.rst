.. title: Win10修改MAC地址
.. slug: win10xiu-gai-macdi-zhi
.. date: 2017-03-31 12:15:05 UTC+08:00
.. tags: win10, Network
.. category: win10
.. link: 
.. description: 
.. type: text

1、打开注册表编辑器，“运行”->“regedit”。

2、找到如下路径，得到下图：

**HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Class\\{4D36E972-E325-11CE-BFC1-08002bE10318}**

.. image:: https://github.com/longlongpicture/myblogpicture/raw/master/modifymac1.PNG

3、右击"0003"->"新建"->"字符串值"->"NetworkAddress"。

4、双击“NetworkAddress”，输入新的MAC地址值，比如“0028F80AF812”。

5、点击“确定”，重启电脑即可。



