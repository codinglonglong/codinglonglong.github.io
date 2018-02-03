.. title: Docker配置开发镜像
.. slug: dockerpei-zhi-kai-fa-jing-xiang
.. date: 2017-01-23 23:08:02 UTC+08:00
.. tags: Docker, flask, Python
.. category: Docker
.. link: 
.. description: 
.. type: text

在主系统上开发，在Docker中部署，在主系统上测试……不需要一手一台电脑，也不需要担心虚拟机占用资源太高，而且不管主系统是Linux、Windows还是MacOS，开发都是一样的……感觉很不错……

1. 新建容器。

        .. code-block:: bash

            docker run --name mypc -i -t -p 8080:8080 -v ~/share/:/usr/development/ ubuntu:14.04 /bin/bash

2. Docker中修改Ubuntu软件源。

        .. code-block:: bash

            vi /etc/apt/sources.list
            :%s/archive.ubuntu/cn.archive.ubuntu/g
            :wq

3. Docker中更新软件源。

        .. code-block:: bash

            apt update

4. Docker中安装Python和Flask。

        .. code-block:: bash

            apt install python
            apt install python-pip
            apt install python-dev
            pip install flask

5. 在主系统目录 **~/share/** 下编写测试网站main.py。

        .. code-block:: python
            :number-lines:

            from flask import Flask
            app = Flask(__name__)

            @app.route('/')
            def hello_world():
                return 'Hello World!'

            if __name__ == '__main__':
                app.run(host="0.0.0.0", port="8080")

6. Docker中运行网站。

        .. code-block:: bash

            cd /usr/development/
            python main.py

7. 主系统上查看效果。

.. image:: https://github.com/longlongpicture/myblogpicture/raw/master/flaskhelloworld.PNG


**注意** 

1. docker run --name mypc -i -t -p 8080:8080 -v ~/share/:/usr/development/ ubuntu:14.04 /bin/bash 中的 **/usr/development/** 不可以是系统已有目录，否则会有权限问题，影响后续的安装。
2. 如果不喜欢使用vim，第二步中可以先安装emacs，再修改/etc/apt/sources.list。




