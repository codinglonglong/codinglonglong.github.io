.. title: Docker创建开发镜像
.. slug: dockerchuang-jian-kai-fa-jing-xiang
.. date: 2017-01-22 02:41:24 UTC+08:00
.. tags: Docker
.. category: Docker
.. link: 
.. description: 
.. type: text

学习完Docker的基本命令，我们来创建一个用于开发的镜像。

**注意** ：Docker里默认无法正常显示中文，只好尽量使用英文了。

*ubuntu:16.04镜像使用apt-get会报错，并且缺少很多工具……所以我们用centos来完成进一步的配置……额……yum也报错……*

尝试了Ubuntu、CentOS、Debian、Fedora几个主流系统的镜像，基本的使用都出现了问题……不太理解为什么docker镜像里最基本的系统工具都没法用……准确地说，对于菜鸟来说，不太会用……

不过还好，不管哪个发行版，有个基本的Linux系统，需要什么工具去http://mirrors.163.com找就可以了。下面以CentOS为例做一下。

1. 创建一个带有共享目录和端口映射的容器。

    .. code-block:: bash

        docker run --name mypc -i -t -p 8080:8080 -v ~/share/:/usr/share/ centos:latest /bin/bash

2. 安装pip。

    .. code-block:: bash

        curl -O https://bootstrap.pypa.io/get-pip.py
        python get-pip.py
        pip install flask

3. 安装net-tools，提供ifconfig。

    .. code-block:: bash

        rpm -Uvh http://mirrors.163.com/centos/7/os/x86_64/Packages/net-tools-2.0-0.17.20131004git.el7.x86_64.rpm

4. 在主系统上编写python程序main.py，存储到用户目录下的share文件夹中。

    .. code-block:: python
        :number-lines:

        from flask import Flask
        app = Flask(__name__)

        @app.route('/')
        def hello_world():
            return 'Hello World!'

        if __name__ == '__main__':
            app.run(host="0.0.0.0", port="8080")

5. 在Docker中切换到共享目录/usr/share/，启动网站。

    .. code-block:: bash

        python main.py

6. 主系统上访问 http://192.168.99.100:8080/，即可看到网站主页。