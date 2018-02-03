.. title: Ubuntu修改root密码
.. slug: ubuntuxiu-gai-rootmi-ma
.. date: 2015-09-15 12:32:12 UTC+08:00
.. tags: Ubuntu
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

Ubuntu修改root密码的方法如下：
::

   long@pc3:/usr/local/lib/python2.7/dist-packages$ sudo passwd
   Enter new UNIX password: 
   Retype new UNIX password: 
   passwd: password updated successfully
   long@pc3:/usr/local/lib/python2.7/dist-packages$ su - root
   Password: 
   root@pc3:~# ls
