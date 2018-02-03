.. title: Supervisor实现Python脚本自启动
.. slug: supervisorshi-xian-pythonjiao-ben-zi-qi-dong
.. date: 2017-02-28 2:06:10 UTC+08:00
.. tags: supervisor
.. category: Python
.. link: 
.. description: 
.. type: text


经过若干小时的反复试验，终于在树莓派上成功部署了homebank[https://codinglonglong.github.io/posts/xiao-jia-shou-zhang-wang-ye-ban-ji-ben-wan-cheng/]，最困难的地方就是配置Supervisor，配置过程中出现了各种错误……


1、安装supervisor。

    ::

        >> sudo pip install supervisor

2、编辑配置文件。

    ::

        >> cd /home/pi/websites/
        >> echo_supervisord_conf > supervisord.conf
        >> sudo supervisord -c supervisord.conf
        >> emacs supervisord.conf
        [inet_http_server]         ; inet (TCP) server disabled by default
        port=0.0.0.0:9999        ; (ip_address:port specifier, *:port for all iface)
        username=user              ; (default is no username (open server))
        password=123               ; (default is no password (open server))

        [program:homebank]
        command=python main.py
        directory=/home/pi/websites/homebank
        

3、启动服务。

    ::

        >> sudo supervisorctl reload
        >> sudo supervisorctl status homebank
        homebank                         RUNNING   pid 2212, uptime 0:02:07

4、设置开机启动。

    ::

        >> sudo emacs /etc/rc.local
        sudo /usr/local/bin/supervisord -c /home/pi/websites/supervisord.conf

5、设置sudo免密。

    ::

        >> sudo visudo
        pi ALL = (ALL)NOPASSWD:ALL

6、重启。

    :: 
    
        >> sudo reboot



