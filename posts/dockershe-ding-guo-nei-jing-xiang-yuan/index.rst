.. title: Docker设定国内镜像源
.. slug: dockershe-ding-guo-nei-jing-xiang-yuan
.. date: 2017-12-19 21:58:48 UTC+08:00
.. tags: Docker
.. category: Docker
.. link: 
.. description: 
.. type: text


1、访问 http://www.daocloud.io/mirror 

2、注册一个账号，登录

3、访问 http://www.daocloud.io/mirror#accelerator-doc

4、点Windows

5、点Copy，将加速地址复制到剪贴板里

6、启动"Docker Quickstart Terminal"

7、输入如下命令

::

    >> docker-machine ssh default
    >> sudo sed -i "s|EXTRA_ARGS='|EXTRA_ARGS='--registry-mirror=加速地址 |g" /var/lib/boot2docker/profile
    >> exit
    >> docker-machine restart default 

8、再执行docker run时就从daocloud上下载系统镜像了

