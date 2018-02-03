.. title: Ubuntu命令行连接wifi
.. slug: ubuntuming-ling-xing-lian-jie-wifi
.. date: 2017-07-19 11:06:54 UTC+08:00
.. tags: Ubuntu, wifi
.. category: Linux
.. link: 
.. description: 
.. type: text

::

    >> cd /usr/local/bin/
    >> cd /home/long
    >> wpa_passphrase SSID PWD > /home/long/wifi.conf
    >> sudo emacs /etc/network/interfaces
    auto wlan0  
    iface wlan0 inet dhcp
    wpa-conf /home/long/wifi.conf
    >> sudo reboot

**注意**

路由器必须要打开DHCP才可以正常连接。

