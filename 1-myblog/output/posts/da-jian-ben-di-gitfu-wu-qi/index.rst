.. title: 搭建本地git服务器
.. slug: da-jian-ben-di-gitfu-wu-qi
.. date: 2015-09-07 18:54:09 UTC+08:00
.. tags: git, Linux
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

搭建本地git服务器的步骤如下：

1、找到一台没人用的电脑，安装上Linux系统，在这里选用的是Ubuntu 14.04。然后配置静态IP：172.16.0.110。

2、安装git服务：
::

    >> sudo apt-get install git

3、创建一个git用户：
::

    >> sudo adduser git

创建git用户之后，远端才可以用git clone **git** @......要不然这里需要换成默认用户名，总觉得有点怪异。

4、建立/home/git/.ssh/authorized_keys文件，将团队每个人的~/.ssh/id_rsa.pub文件复制到上述文件中，一行一个。

5、在/srv目录建立一个git仓库：
::

    >> cd /srv
    >> sudo git init --bare ourwiki.git

6、修改git仓库的所属者：
::

    >> sudo chown -R git:git ourwiki.git

7、这时团队成员通过如下命令即可克隆ourwiki项目了：
::

    >> git clone git@172.16.0.110:/srv/ourwiki.git

