.. title: 忘记Mysql密码
.. slug: wang-ji-mysqlmi-ma
.. date: 2015-09-07 09:48:46 UTC+08:00
.. tags: Mysql
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text


1、修改配置文件
::

   >> long@happytime:~$ sudo emacs /etc/mysql/my.cnf

在[mysqld]部分加入： skip-grant-tables，然后保存退出。

2、重新启动mysql服务
::

   >> sudo service mysql restart

3、进入mysql修改密码
::

   >> long@happytime:~$ mysql
   >> Welcome to the MySQL monitor.  Commands end with ; or \g.
   >> Your MySQL connection id is 36
   >> Server version: 5.5.43-0ubuntu0.14.04.1 (Ubuntu)
   >> 
   >> Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.
   >> 
   >> Oracle is a registered trademark of Oracle Corporation and/or its
   >> affiliates. Other names may be trademarks of their respective
   >> owners.
   >> 
   >> Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
   >> 
   >> mysql> use mysql;
   >> Reading table information for completion of table and column names
   >> You can turn off this feature to get a quicker startup with -A
   >> 
   >> Database changed
   >> mysql> update user set Password=password('newpassword') where User='root';
   >> Query OK, 4 rows affected (0.00 sec)
   >> Rows matched: 4  Changed: 4  Warnings: 0
   >> 
   >> mysql> flush privileges;
   >> Query OK, 0 rows affected (0.00 sec)
   >> 
   >> mysql> quit
   >> Bye


4、记得把配置文件改回来

5、重启mysql服务   
