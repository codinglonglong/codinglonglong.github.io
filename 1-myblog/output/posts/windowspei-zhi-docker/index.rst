.. title: Windows配置Docker
.. slug: windowspei-zhi-docker
.. date: 2017-01-21 17:27:00 UTC+08:00
.. tags: Windows, Docker
.. category: Docker
.. link: 
.. description: 
.. type: text

因为新笔记本的无线网卡和声卡比较新，目前的Linux发行版都无法很好地支持，所以只好先用Windows来进行开发了……

第一步，在Windows上部署Linux开发环境，首先考虑到的是用Docker。

1. 安装docker-toolbox。访问下载安装： https://www.docker.com/products/docker-toolbox
2. 在开始菜单双击运行Docker Quickstart Terminal，等待……………………直到出现

    .. code-block:: bash
        :number-lines:

        docker is configured to use the default machine with IP 192.168.99.100
        For help getting started, check out the docs at https://docs.docker.com

        Start interactive shell

        long@DESKTOP-N79DL8P MINGW64 ~
        $

3. 运行 **docker pull ubuntu:16.04** 。
4. 运行 **docker run -it --rm ubuntu:16.04 bash** ，进入ubuntu的交互环境。


