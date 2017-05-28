.. title: Docker配置vuejs开发环境
.. slug: dockerpei-zhi-vuejskai-fa-huan-jing
.. date: 2017-03-13 20:36:24 UTC+08:00
.. tags: Docker, vuejs
.. category: javascript
.. link: 
.. description: 
.. type: text


**为了防止出现问题，需要先用管理员权限打开Docker终端。**


1、安装wget，下载最新版nodejs。

    ::

        >> apt udpate
        >> apt install wget
        >> cd ~
        >> wget https://nodejs.org/dist/v7.7.2/node-v7.7.2-linux-x64.tar.xz

2、安装nodejs。

    ::

        >> apt install xz-utils
        >> xz -d node-v7.7.2-linux-x64.tar.xz
        >> tar -xvf node-v7.7.2-linux-x64.tar
        >> apt install emacs
        >> emacs ~/.bashrc
        export PATH=$PATH:/root/node-v7.7.2-linux-x64/bin/
        >> source ~/.bashrc

3、安装vue和vue-cli。

    ::

        >> npm install --global vue vue-cli

4、创建新项目。

    ::

        >> cd ~
        >> mkdir development
        >> cd development
        >> apt install git
        >> vue init webpack test
        >> cd test
        >> npm install
        >> npm run dev

5、主系统访问 http://192.168.99.100:8080 即可。


**注意** 

如果容器如下这样启动的话：

::

    >> docker run --name t1 -i -t -p 10001:8080  ~/share/:/usr/development/ ubuntu:14.04 /bin/bash


访问 http://192.168.99.100:10001 才可以看到虚拟机里的网站。

虚拟机里的网站用8080端口，那么主系统需要访问192.168.99.100的10001端口。

192.168.99.100是在docker终端启动时显示出来的。

