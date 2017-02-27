.. title: Raspberry设置静态IP
.. slug: raspberryshe-zhi-jing-tai-ip
.. date: 2017-02-27 19:45:07 UTC+08:00
.. tags: Raspberry, Linux
.. category: Raspberry
.. link: 
.. description: 
.. type: text

1、编辑网络配置文件。

    ::

        >> sudo vi /etc/network/interfaces
        iface eth0 inet static
        address 192.168.1.254
        netmask 255.255.255.0
        gateway 192.168.1.1
        >> sudo service networking restart


2、重启系统和路由器。


**如果不行的话，试试把路由器也设置成静态地址绑定……**

