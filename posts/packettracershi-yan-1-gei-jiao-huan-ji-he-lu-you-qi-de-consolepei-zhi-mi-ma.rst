.. title: PacketTracer实验1——给交换机和路由器的Console配置密码
.. slug: packettracershi-yan-1-gei-jiao-huan-ji-he-lu-you-qi-de-consolepei-zhi-mi-ma
.. date: 2023-04-10 21:31:45 UTC+08:00
.. tags: PacketTracer
.. category: 网络设备
.. link: 
.. description: 
.. type: text



1、用控制台连线，连接PC机的 RS232 端口和路由器的 Console 端口。

.. image:: /images/7835452a-78f8-46f1-bc9e-f4b500117c40.png

.. TEASER_END

2、单击PC机，打开“桌面”，点击“终端”。

.. image:: /images/093ed9e6-75e5-40fa-b55e-c4b370c27e3a.png

3、点击“确定”。

.. image:: /images/9b690503-a415-49f1-b2b5-f209d5096cd9.png

4、输入 no ，回车。

.. image:: /images/676039eb-5faa-4232-8572-cdb1e4093535.png

5、配置如下内容：

.. code-block:: text
    :number-lines:


    Router>
    Router>en                            【进入特权模式】
    Router#conf t                        【进入全局配置模式】
    Router(config)#line console 0        【配置Console 0接口】
    Router(config-line)#password 123456  【密码123456】
    Router(config-line)#login            【允许通过本地登录】
    Router(config-line)#exit
    Router(config)#exit
    Router#write                         【保存配置】
    Building configuration...
    [OK]
    Router#reload                        【重启路由器】
    Proceed with reload? [confirm]

6、待路由器重启完成后，再次进入终端，发现需要输入密码才可以配置路由器。

.. image:: /images/80a38014-0bf6-4b9a-89c1-8180bcd28f5f.png


**注意：输入密码时没有回显【 不显示密码，也不显示星号，但实际已经输入了，输入完成按回车键 】**

交换机的配置方法和路由器相同，参考以上配置即可。

