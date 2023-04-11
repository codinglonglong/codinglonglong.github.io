.. title: PacketTracer实验2——给路由器配置telnet远程登录
.. slug: packettracershi-yan-2-gei-lu-you-qi-pei-zhi-telnetyuan-cheng-deng-lu
.. date: 2023-04-10 22:56:45 UTC+08:00
.. tags: PacketTracer
.. category: 网络设备
.. link: 
.. description: 
.. type: text


1、实验拓扑图。

.. image:: /images/5e3d4e2d-dbfa-4a03-a0b4-0b2095584581.png

.. TEASER_END


2、参考文章  https://codinglonglong.github.io/posts/packettracershi-yan-1-gei-jiao-huan-ji-he-lu-you-qi-de-consolepei-zhi-mi-ma.html 

使用 PC0 通过 终端 对 路由器 进行如下配置。

.. code-block:: text
    :number-lines:

    Router>en                                                       
    Router#conf t
    Router(config)#int GigabitEthernet 0/0/0                        【配置 GE 0/0/0 接口】
    Router(config-if)#ip address 192.168.1.253 255.255.255.0        【配置该接口IP地址】
    Router(config-if)#no shutdown                                   【打开该接口】
    Router(config-if)#exit
    Router(config)#ip default-gateway 192.168.1.254                 【配置路由器的默认网关，用于日后与其他网段主机通信】
    Router(config)#username test password 123                       【设置登录用户名和密码】
    Router(config)#line vty 0 4                                     【配置虚拟终端 0~4 线路】
    Router(config-line)#login local                                 【允许本地登录】
    Router(config-line)#exit
    Router(config)#enable password 123456                           【配置特权密码，如果用加密模式需要使用 enable secret 123456】
    Router(config)#exit
    Router#


3、给 PC2 配置IP地址。

.. image:: /images/eb602528-882a-4234-903d-3f702635135a.png


.. image:: /images/717354cb-73a5-48b3-8992-68e12cc61152.png


4、使用 PC2 的命令提示符通过telnet命令测试远程登录路由器。

.. image:: /images/a76d927d-5cce-4e69-aed1-b0fc8a400465.png

.. image:: /images/367a8173-d9af-4ebb-9fcc-460a3fe54aad.png

图中 show run 命令的作用是显示当前生效配置。

