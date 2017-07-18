.. title: Linux添加用户和切换用户
.. slug: linuxtian-jia-yong-hu-he-qie-huan-yong-hu
.. date: 2015-09-08 09:16:20 UTC+08:00
.. tags: Linux
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

添加用户
::

   >> sudo adduser long

这时系统会交互输入一些基本信息，按需要输入就可以。但是新添加的用户默认没有执行sudo的权限。
   
赋予用户执行sudo的权限
::

   >> sudo usermod  -a -G sudo long

-------

切换用户   
::

   >> su - long

这样就进入long的用户环境了，毕竟一直用root工作不是很安全，还是建立一个普通用户比较保险。

-------

这里再多说一点关于su -、su和sudo的区别：

**su -** : 完全意义上的切换用户，包括环境变量配置之类的。

**su** : 只是切换了当前工作的用户，环境变量配置之类的不变。

**sudo** : 赋予用户执行部分高级功能的权限。
