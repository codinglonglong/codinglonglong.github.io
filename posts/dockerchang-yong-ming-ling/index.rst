.. title: Docker常用命令
.. slug: dockerchang-yong-ming-ling
.. date: 2017-01-21 20:13:52 UTC+08:00
.. tags: Docker
.. category: Docker
.. link: 
.. description: 
.. type: text

1. 创建容器。

    .. code-block:: bash

        docker run --name mypc -it ubuntu:16.04 /bin/bash

经过实验，目前只有这样创建的容器可以在后边正常start。

2. 查看已有容器及其状态。

    .. code-block:: bash

        docker ps -a

3. 启动已有容器。

    .. code-block:: bash

        docker start mypc 

4. 登陆正在运行的容器。

    .. code-block:: bash

        docker exec -it mypc /bin/bash

5. 关闭正在运行的容器。

    .. code-block:: bash

        docker stop mypc 

6. 删除容器。

    .. code-block:: bash

        docker rm mypc

**注意** ：重启电脑之前，记得先把VirtualBox里边的虚拟机正常关机，否则等重启回来，容器可能就找不到了。