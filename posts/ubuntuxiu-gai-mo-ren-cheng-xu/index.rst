.. title: Ubuntu修改默认程序
.. slug: ubuntuxiu-gai-mo-ren-cheng-xu
.. date: 2015-09-07 10:48:45 UTC+08:00
.. tags: Ubuntu
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

Ubuntu默认的PDF阅读器Evince没有KDE内置的Okular功能强大，安装上Okular后，我们需要修改系统默认程序。

修改方法如下：

::

   >> sudo gedit /etc/gnome/defaults.list

将 **application/pdf=evince.desktop** 替换成 **application/pdf=okular.desktop** 。

如果需要替换其他功能的默认程序，按照类似的操作即可。
