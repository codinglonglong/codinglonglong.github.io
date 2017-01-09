.. title: 管理多个git账户
.. slug: guan-li-duo-ge-gitzhang-hu
.. date: 2017-01-09 21:28:59 UTC+08:00
.. tags: git, 版本管理
.. category: git
.. link: 
.. description: 
.. type: text

因为博客用了两个github账户，一个放文章，一个放图片，所以出现了两个git账户同时存在的问题。这时可以通过如下的方法解决冲突：

1. 生成两个ssh key.

.. code-block:: bash

    >> ssh-keygen -t rsa -C "email address 1"
    >> ssh-keygen -t rsa -C "email address 2"

2. 添加上一步生成的两个ssh key.

.. code-block:: bash

    >> ssh-add ~/.ssh/id_rsa1
    >> ssh-add ~/.ssh/id_rsa2

3. 创建配置文件.
        
.. code-block:: bash
        
    >> touch config

.. code-block:: bash
   :number-lines:
   
   # github1
   Host github1
        HostName github.com
        PreferredAuthentications publickey
        IdentityFile ~/.ssh/id_rsa1
   # github2
   Host github2
        HostName github.com
        PreferredAuthentications publickey
        IdentityFile ~/.ssh/id_rsa2

4. 测试.

.. code-block:: bash

    >> ssh -T git@github1
    >> ssh -T git@github2

**注意** 

1. 过程之中遇到yes或者no，都输入yes。
2. 生成的ssh key别忘了放进github的“设置”里，并且注意结尾不能有回车。


