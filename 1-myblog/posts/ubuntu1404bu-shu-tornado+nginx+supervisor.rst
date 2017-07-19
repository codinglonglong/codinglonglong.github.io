.. title: Ubuntu14.04部署Tornado+Nginx+Supervisor
.. slug: ubuntu1404bu-shu-tornado+nginx+supervisor
.. date: 2015-09-07 18:32:39 UTC+08:00
.. tags: Tornado, nginx, supervisor, Ubuntu, Python
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

本文主要讲述如何在Ubuntu上部署用Tornado编写的网站，涉及进程管理工具Supervisor和服务器Nginx。

前提：网站使用Python编写，采用Tornado框架和Mysql数据库，要部署网站的机器deploy为Ubuntu14.04系统，静态IP地址为192.168.122.150，要部署的网站为reciteword.tar.gz

1、安装emacs
::

   >> sudo apt-get install emacs

2、设定静态IP
::

   >> sudo emacs /etc/network/interfaces

3、修改eth0部分
::

   auto eth0
   iface eth0 inet static
   address 192.168.122.150
   netmask 255.255.255.0
   gateway 192.168.122.1
   dns-nameserver 202.98.198.167

4、保存文件，重启机器
::

   >> sudo reboot

5、下载部署相关软件
::

   >> sudo apt-get install mysql-server mysql-client python3-tornado python3-mysql.connector emacs nginx python-pip python3-pip

6、安装beautifulsoup4（这个是网站运行需要的）
::

   >> sudo pip3 install beautifulsoup4

7、下载supervisor
::

   >> wget https://pypi.python.org/packages/source/s/supervisor/supervisor-3.1.3.tar.gz

8、解压网站代码和supervisor
::

   >> tar zxvf reciteword.tar.gz
   >> tar zxvf supervisor-3.1.3.tar.gz

.. teaser_end

9、启动数据库
::

   >> sudo mysqld

10、开启一个新的终端，生成数据库
::

   >> sudo mysql -u root -p
   mysql> source /home/long/reciteword/db/recitewordbase.sql;

11、安装supervisor
::

   >> cd supervisor-3.1.3/
   >> sudo python setup.py install

12、编写supervisord.conf配置文件
::

   >> cd /home/long/reciteword/
   >> echo_supervisord_conf > supervisord.conf

在supervisord.conf最后追加

::

   [program:reciteword-8001]
   command=python3 /home/long/reciteword/main.py --port=8001
   directory=/home/long/reciteword
   autorestart=true
   redirect_stderr=true
   stdout_logfile=/home/long/reciteword/reciteword_server-8001.log
   stdout_logfile_maxbytes=500MB
   stdout_logfile_backups=50
   stdout_capture_maxbytes=1MB
   stdout_events_enabled=false
   loglevel=warn

   [program:reciteword-8002]
   command=python3 /home/long/reciteword/main.py --port=8002
   directory=/home/long/reciteword
   autorestart=true
   redirect_stderr=true
   stdout_logfile=/home/long/reciteword/reciteword_server-8002.log
   stdout_logfile_maxbytes=500MB
   stdout_logfile_backups=50
   stdout_capture_maxbytes=1MB
   stdout_events_enabled=false
   loglevel=warn

   [program:reciteword-8003]
   command=python3 /home/long/reciteword/main.py --port=8003
   directory=/home/long/reciteword
   autorestart=true
   redirect_stderr=true
   stdout_logfile=/home/long/reciteword/reciteword_server-8003.log
   stdout_logfile_maxbytes=500MB
   stdout_logfile_backups=50
   stdout_capture_maxbytes=1MB
   stdout_events_enabled=false
   loglevel=warn

   [program:reciteword-8004]
   command=python3 /home/long/reciteword/main.py --port=8004
   directory=/home/long/reciteword
   autorestart=true
   redirect_stderr=true
   stdout_logfile=/home/long/reciteword/reciteword_server-8004.log
   stdout_logfile_maxbytes=500MB
   stdout_logfile_backups=50
   stdout_capture_maxbytes=1MB
   stdout_events_enabled=false


13、启动supervisor
::

   >> supervisord -c supervisord.conf

14、修改nginx配置文件
::

   >> cd /etc/nginx/sites-available
   >> sudo emacs default

注释掉所有内容

::

   >> cd /etc/nginx
   >> sudo emacs nginx.conf

在http段追加以下配置：

::

    proxy_next_upstream error;
    upstream tornadoes {
        server 192.168.122.150:8001;
        server 192.168.122.150:8002;
        server 192.168.122.150:8003;
        server 192.168.122.150:8004;
        ip_hash;
     }
    server {
        listen 80;
        server_name 192.168.122.150;
        
        location / {
            proxy_pass_header Server;
            proxy_set_header Host $http_host;
            proxy_redirect off;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Scheme $scheme;
            proxy_pass http://tornadoes;
         }
    }

15、保存，重启nginx
::

   >> sudo service nginx restart

16、浏览器访问192.168.122.150即可

