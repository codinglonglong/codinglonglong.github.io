.. title: 通过privoxy实现http和https代理
.. slug: tong-guo-privoxyshi-xian-httphe-httpsdai-li
.. date: 2017-03-03 20:14:40 UTC+08:00
.. tags: privoxy, proxy
.. category: Linux
.. link: 
.. description: 
.. type: text


有的时候为了完成某些测试，我们需要用到代理来更换IP地址，以下是可选的一种方法。


1、安装privoxy。

    ::

        >> sudo apt install privoxy

2、编辑配置文件。

    ::

        >> sudo emacs /etc/privoxy/config
        listen-address localhost:8118
        forward-socks5 / 127.0.0.1:1080 .

3、重启服务。

    ::

        >> sudo service privoxy restart
        >> sudo reboot
