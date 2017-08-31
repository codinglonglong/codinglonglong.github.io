.. title: Ubuntu开机进入命令行模式
.. slug: ubuntukai-ji-jin-ru-ming-ling-xing-mo-shi
.. date: 2015-09-14 22:05:34 UTC+08:00
.. tags: Ubuntu
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

打开终端执行如下命令：
::

   >> sudo emacs /etc/default/grub
   GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"
   >> sudo update-grub

重启就直接进入命令行界面了。
