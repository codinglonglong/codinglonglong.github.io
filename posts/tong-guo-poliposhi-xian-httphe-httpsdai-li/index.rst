.. title: 通过polipo实现http和https代理
.. slug: tong-guo-poliposhi-xian-httphe-httpsdai-li
.. date: 2017-03-04 03:50:32 UTC+08:00
.. tags: polipo, proxy
.. category: Linux
.. link: 
.. description: 
.. type: text

反复试验也没能让privoxy在树莓派上自启动，只好换一个软件来试验了……

1、安装polipo。

    ::

        >> sudo apt install polipo

2、编辑配置文件。

    ::

        >> sudo emacs /etc/polipo/config
        proxyAddress="0.0.0.0"
        proxyPort=8228
        socksParentProxy="127.0.0.1:2080"
        socksProxyType=socks5

3、重启服务。

    ::

        >> sudo service polipo restart
        >> sudo reboot


结果显示，polipo在树莓派上不需要任何进一步的配置就可以自动启动服务。
