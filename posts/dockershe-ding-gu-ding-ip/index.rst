.. title: Docker设定固定IP
.. slug: dockershe-ding-gu-ding-ip
.. date: 2017-05-14 14:55:30 UTC+08:00
.. tags: Docker
.. category: Docker
.. link: 
.. description: 
.. type: text


1. 新建自定义网络。

    .. code-block:: bash

        >> docker network create --subnet=172.16.0.0/16 testnet


2. 创建虚拟机。

    .. code-block:: bash

        >>  docker run --name t1 -i -t --net=testnet --ip=172.16.0.111 -p 8080:8080 -v ~/share/:/usr/development/ ubuntu:14.04 /bin/bash
        >>  docker run --name t2 -i -t --net=testnet --ip=172.16.0.112 -p 8081:8081 -v ~/share/:/usr/development/ ubuntu:14.04 /bin/bash


3. 进入虚拟机，查看当前IP。

    .. code-block:: bash

        >> docker exec -it t1 /bin/bash
        >> root@2ef31a06d8f8:/# ifconfig
        eth0      Link encap:Ethernet  HWaddr 02:42:ac:10:00:6f
                inet addr:172.16.0.111  Bcast:0.0.0.0  Mask:255.255.0.0
                inet6 addr: fe80::42:acff:fe10:6f/64 Scope:Link
                UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
                RX packets:22 errors:0 dropped:0 overruns:0 frame:0
                TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
                collisions:0 txqueuelen:0
                RX bytes:1716 (1.7 KB)  TX bytes:1026 (1.0 KB)

        lo        Link encap:Local Loopback
                inet addr:127.0.0.1  Mask:255.0.0.0
                inet6 addr: ::1/128 Scope:Host
                UP LOOPBACK RUNNING  MTU:65536  Metric:1
                RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                collisions:0 txqueuelen:1
                RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
        >> docker exec -it t2 /bin/bash
        >> root@a9cd9a699b05:/# ifconfig
        eth0      Link encap:Ethernet  HWaddr 02:42:ac:10:00:70
                inet addr:172.16.0.112  Bcast:0.0.0.0  Mask:255.255.0.0
                inet6 addr: fe80::42:acff:fe10:70/64 Scope:Link
                UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
                RX packets:14 errors:0 dropped:0 overruns:0 frame:0
                TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
                collisions:0 txqueuelen:0
                RX bytes:1068 (1.0 KB)  TX bytes:1166 (1.1 KB)

        lo        Link encap:Local Loopback
                inet addr:127.0.0.1  Mask:255.0.0.0
                inet6 addr: ::1/128 Scope:Host
                UP LOOPBACK RUNNING  MTU:65536  Metric:1
                RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                collisions:0 txqueuelen:1
                RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


4. 重启之后，IP地址依然保持之前的设置，并且可以相互ping通。
