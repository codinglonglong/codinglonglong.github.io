.. title: Docker中配置Flask-Sqlalchemy和Mysql
.. slug: dockerzhong-pei-zhi-flask-sqlalchemyhe-mysql
.. date: 2017-01-25 13:37:42 UTC+08:00
.. tags: Flask-Sqlalchemy, Mysql, Python, Docker
.. category: Python
.. link: 
.. description: 
.. type: text

继文章 https://codinglonglong.github.io/posts/dockerpei-zhi-kai-fa-jing-xiang/ 之后，我们进一步配置数据库的部分。

1、Docker安装Mysql。

    .. code-block:: bash

        apt install mysql-server mysql-client

2、Docker下载安装mysql-connector-python。

    .. code-block:: bash

        apt install curl
        curl -O https://cdn.mysql.com/Downloads/Connector-Python/mysql-connector-python-2.1.5.tar.gz
        tar zxvf mysql-connector-python-2.1.5.tar.gz
        cd mysql-connector-python-2.1.5
        python setup.py install

3、Docker安装Flask-Sqlalchemy和Flask-Script。

    .. code-block:: bash

        pip install flask-sqlalchemy
        pip install flask-script

4、为已有容器添加端口。

    .. code-block:: bash

        docker commit mypc newpc
        docker stop mypc
        docker run --name mynewpc -i -t -p 13306:3306 -p 8080:8080 -v ~/share/:/usr/development/  newpc /bin/bash

5、Docker登录Mysql数据库。

    .. code-block:: bash

        mysql -u root -p
        create database test;
        grant all privileges on *.* to root@'192.168.99.1' identified by 'root' with grant option;
        flush privileges;
        exit

6、Docker修改配置文件，我习惯用emacs，也可以用vim。

    .. code-block:: bash

        apt install emacs
        apt-get install -f
        emacs /etc/mysql/my.cnf
        bind-address            = 0.0.0.0
        C-x C-s
        C-x C-c

7、重启mysql服务。

    .. code-block:: bash

        sudo service mysql stop
        mysqld

8、主系统编辑测试网站main.py。

        .. code-block:: python
            :number-lines:

            from flask import Flask
            from flask.ext.script import Manager
            from flask.ext.sqlalchemy import SQLAlchemy

            app = Flask(__name__)
            app.config['SQLALCHEMY_DATABASE_URI'] = 'mysql+mysqlconnector://root:root@127.0.0.1:3306/test?charset=utf8'

            db = SQLAlchemy(app)
            manager = Manager(app)

            class User(db.Model):
                __tablename__ = 'users'
                id = db.Column(db.Integer, primary_key=True)
                username = db.Column(db.String(80), unique=True)
                email = db.Column(db.String(320), unique=True)
                password = db.Column(db.String(32), nullable=False)

            if __name__ == '__main__':
                db.create_all()
                manager.run()


9、开一个新的Docker terminal，启动测试网站。

    .. code-block:: bash

        cd /usr/development
        python main.py runserver

10、主系统上打开MySQL Workbench，访问数据库。Hostname：192.168.99.100，Port：13306，Password：root。

.. image:: https://github.com/longlongpicture/myblogpicture/raw/master/mysqlworkbench.PNG

**注意** 

修改bind-address = 0.0.0.0非常重要，否则主系统访问不到Docker中的数据库。






