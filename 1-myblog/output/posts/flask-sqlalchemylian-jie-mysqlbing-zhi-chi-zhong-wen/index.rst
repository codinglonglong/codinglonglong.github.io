.. title: Flask-Sqlalchemy连接Mysql并支持中文
.. slug: flask-sqlalchemylian-jie-mysqlbing-zhi-chi-zhong-wen
.. date: 2017-01-30 21:36:46 UTC+08:00
.. tags: Flask-Sqlalchemy, Mysql
.. category: Python
.. link: 
.. description: 
.. type: text

按照文章 https://codinglonglong.github.io/posts/dockerzhong-pei-zhi-flask-sqlalchemyhe-mysql/ 配置好数据库，在默认使用Flask-Sqlalchemy连接Mysql时，如果插入的数据是中文，会保存成问号。如果要正常保存中文，需要注意以下四点：

1、 .py文件本身是UTF-8的编码，这可以在开发工具的“文件编码”功能中进行查看。

2、 .py文件开头加上 **# -*-coding:utf-8-*-**。

3、 连接字符串采用如下格式，注意最后的部分：

        .. code-block:: python

            dbconnection = 'mysql+mysqlconnector://username:password@host:port/dbname?charset=utf8'

4、 默认Mysql是latin-1的编码，如下：

        .. code-block:: bash
            :number-lines:

            mysql> status           12
            Current database:
            Current user:.14 Distribroot@localhostebian-linux-gnu (x86_64) using readline 6.3
            SSL:                    Not in use
            Current pager:          ''dout
            Using delimiter:        5.5.54-0ubuntu0.14.04.1 (Ubuntu)
            Protocol version:       Localhost via UNIX socket
            Server characterset:    latin1
            Client characterset:    latin1
            UNIX socket:cterset:    3 min 58 secqld/mysqld.sock
            Uptime:
            Threads: 3  Questions: 324  Slow queries: 0  Opens: 45  Flush tables: 1  Open tables: 31  Queries per second avg: 1.361
            --------------

要通过修改配置文件，改成utf-8编码。

        .. code-block:: bash

            emacs /etc/mysql/my.cnf
            [mysqld]
            character_set_server = utf8
            [client]
            default-character-set = utf8
            [mysql]
            default-character-set = utf8

            service mysql stop
            mysqld

重启服务之后，可以看到：

        .. code-block:: bash
            :number-lines:

            mysql> status           1
            Current database:
            Current user:.14 Distribroot@localhostebian-linux-gnu (x86_64) using readline 6.3
            SSL:                    Not in use
            Current pager:          ''dout
            Using delimiter:        5.5.54-0ubuntu0.14.04.1 (Ubuntu)
            Protocol version:       Localhost via UNIX socket
            Server characterset:    utf8
            Client characterset:    utf8
            UNIX socket:cterset:    6 secrun/mysqld/mysqld.sock
            Uptime:
            Threads: 1  Questions: 5  Slow queries: 0  Opens: 33  Flush tables: 1  Open tables: 26  Queries per second avg: 0.833
            --------------


满足上述四点之后，删除掉原来包含问号的数据库，然后重新创建数据库，运行程序，可以看到中文被正常处理了。

.. image:: https://github.com/longlongpicture/myblogpicture/raw/master/mysqlchinese.PNG

