.. title: Ubuntu14.04关闭蓝牙
.. slug: ubuntu1404guan-bi-lan-ya
.. date: 2015-09-21 21:29:28 UTC+08:00
.. tags: Ubuntu
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

一般很少用蓝牙，开着又费电。

在Ubuntu14.04中默认关闭蓝牙的方法：
::

   >> sudo emacs /etc/rc.local
   rfkill block bluetooth
   exit 0
   >> sudo reboot


