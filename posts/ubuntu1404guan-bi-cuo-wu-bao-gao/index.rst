.. title: Ubuntu14.04关闭错误报告
.. slug: ubuntu1404guan-bi-cuo-wu-bao-gao
.. date: 2015-09-21 21:25:41 UTC+08:00
.. tags: Ubuntu
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

错误报告总是弹出来，不知道什么问题，又无法解决问题，不如直接关掉。

Ubuntu14.04关闭错误报告的方法：
::

   >> sudo emacs /etc/default/apport
   enabled=0
   >> sudo reboot


