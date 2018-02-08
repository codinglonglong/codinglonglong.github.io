.. title: Ubuntu14.04部署分布式计算框架Dpark（1）
.. slug: ubuntu1404bu-shu-fen-bu-shi-ji-suan-kuang-jia-dpark1
.. date: 2015-09-14 22:10:25 UTC+08:00
.. tags: 分布式, Ubuntu14.04部署分布式计算框架Dpark, Dpark, Moosefs, Beansdb, Mesos, kvm
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

所用到的工具参考: https://codinglonglong.github.io/posts/fen-bu-shi-xi-tong-xiang-guan-ruan-jian-de-xia-zai-di-zhi/

1、分别在三台机器上安装Ubuntu Desktop 14.04.3，并设定静态IP，参考文章 https://codinglonglong.github.io/posts/ubuntu1404bu-shu-tornado%2Bnginx%2Bsupervisor/

2、分别在三台机器上安装ssh
::

   >> sudo apt-get install ssh openssh-server openssh-client

**在pc3上**

3、搭建内存数据库
::

   >> sudo apt-get update
   >> sudo apt-get install git
   >> sudo apt-get install g++ gcc build-essential gfortran
   >> git clone https://github.com/douban/beansdb
   >> sudo apt-get install autoconf automake libtool
   >> cd beansdb/
   >> sudo ./autogen.sh
   >> ./configure && sudo make && sudo make install
   >> sudo cp beansdb_log.conf /etc/
   >> sudo mkdir /mnt/beansdb

4、建立自启动脚本
::

   >> sudo apt-get install emacs
   >> cd /usr/local/bin
   >> sudo emacs startbeansdb
   beansdb -u root -H /mnt/beansdb -p 7900 -d
   >> sudo chmod 777 startbeansdb

5、设定无密码启动
::

   >> sudo visudo
   long ALL=NOPASSWD:/usr/local/bin/startbeansdb

6、安装beansdb的python接口
::

   >> sudo cp /home/long/beansdb/python/dbclient.py /usr/local/lib/python2.7/dist-packages/
   >> wget https://launchpad.net/libmemcached/1.0/1.0.18/+download/libmemcached-1.0.18.tar.gz
   >> tar zxvf libmemcached-1.0.18.tar.gz
   >> cd libmemcached-1.0.18/
   >> ./configure
   >> sudo make
   >> sudo make install
   >> git clone https://github.com/douban/python-libmemcached
   >> cd python-libmemcached/
   >> sudo apt-get install python-pip python-dev
   >> sudo python setup.py install
   >> emacs ~/.profile
   export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
   >> source ~/.profile

7、搭建分布式文件系统服务器
::

   >> wget http://nchc.dl.sourceforge.net/project/fuse/fuse-2.X/2.9.4/fuse-2.9.4.tar.gz
   >> wget http://ppa.moosefs.com/src/moosefs-2.0.73-1.tar.gz
   >> wget http://zlib.net/zlib-1.2.8.tar.gz
   >> tar zxvf fuse-2.9.4.tar.gz && cd fuse-2.9.4 && ./configure --prefix=/usr && sudo make && sudo make install && cd ..
   >> tar zxvf zlib-1.2.8.tar.gz && cd zlib-1.2.8 && ./configure && sudo make && sudo make install && cd ..
   >> sudo useradd mfs -M -s /sbin/nologin
   >> sudo apt-get install libpcap-dev pkg-config
   >> tar zxvf moosefs-2.0.73-1.tar.gz && cd moosefs-2.0.73 && ./configure --prefix=/usr/local/mfs --with-default-user=mfs --with-default-group=mfs --enable-mfsmount && sudo make && sudo make install
   >> cd /usr/local/mfs/etc/mfs
   >> sudo cp mfsmaster.cfg.dist mfsmaster.cfg
   >> sudo emacs mfsmaster.cfg
   MATOCS_LISTEN_HOST = 192.168.1.203
   >> sudo cp mfsexports.cfg.dist mfsexports.cfg
   >> sudo cp mfstopology.cfg.dist mfstopology.cfg
   >> cd /usr/local/mfs/etc/mfs
   >> sudo cp mfschunkserver.cfg.dist mfschunkserver.cfg
   >> sudo emacs mfschunkserver.cfg
   MASTER_HOST = 192.168.1.203
   >> sudo cp mfshdd.cfg.dist mfshdd.cfg
   >> sudo emacs mfshdd.cfg
   # 删除Examples:以下的内容
   # 在最后添加
   /usr/local/mfs/var/mfs
   >> sudo chown -R mfs:mfs /usr/local/mfs/var/mfs
   >> cd /usr/local/mfs/etc/mfs
   >> sudo cp mfsmount.cfg.dist mfsmount.cfg
   >> sudo emacs mfsmount.cfg
   # Example:
   #
   /mnt/mfs
   >> sudo mkdir /mnt/mfs
   >> sudo chown -R mfs:mfs /mnt/mfs

8、建立自启动脚本
::

   >> cd /usr/local/bin
   >> sudo emacs startmfsmaster
   cd /usr/local/mfs/sbin
   ./mfsmaster -a
   >> sudo chmod 777 startmfsmaster
   >> sudo emacs startmfscgi
   cd /usr/local/mfs/sbin
   ./mfscgiserv
   >> sudo chmod 777 startmfscgi
   >> cd /usr/local/bin
   >> sudo emacs startmfschunk
   cd /usr/local/mfs/sbin/
   ./mfschunkserver start
   >> sudo chmod 777 startmfschunk
   >> cd /usr/local/bin
   >> sudo emacs startmfsmount
   cd /usr/local/mfs/bin/
   ./mfsmount -H 192.168.1.203 -o nonempty
   >> sudo chmod 777 startmfsmount

9、设定无密码启动
::

   >> sudo visudo
   long ALL=NOPASSWD:/usr/local/bin/startmfsmaster
   long ALL=NOPASSWD:/usr/local/bin/startmfscgi
   long ALL=NOPASSWD:/usr/local/bin/startmfschunk
   long ALL=NOPASSWD:/usr/local/bin/startmfsmount

10、安装分布式资源调度框架
::

   >> wget http://archive.apache.org/dist/mesos/0.22.1/mesos-0.22.1.tar.gz  (这里的版本最高就到0.22.1，要不然pymesos无法支持)
   >> tar zxf mesos-0.22.1.tar.gz
   >> sudo apt-get install build-essential openjdk-6-jdk python-dev python-boto libcurl4-nss-dev libsasl2-dev maven libapr1-dev libsvn-dev autoconf libtool
   >> cd mesos-0.22.1
   >> ./bootstrap
   >> mkdir build
   >> cd build
   >> ../configure --prefix=/home/long/mesos
   >> sudo make
   >> sudo make install

11、建立自启动脚本
::

   >> cd /usr/local/bin
   >> sudo emacs startmesosmaster
   cd /home/long/mesos/sbin
   ./mesos-master --ip=192.168.1.203 --work_dir=/var/lib/mesos --quiet &
   >> sudo chmod 777 startmesosmaster
   >> sudo emacs startmesosslave
   cd /home/long/mesos/sbin
   ./mesos-slave --master=192.168.1.203:5050 --quiet &
   >> sudo chmod 777 startmesosslave

12、设定无密码启动
::

   >> sudo visudo
   long ALL=NOPASSWD:/usr/local/bin/startmesosmaster
   long ALL=NOPASSWD:/usr/local/bin/startmesosslave

13、安装pymesos
::

   >> git clone https://github.com/douban/pymesos.git
   >> cd pymesos
   >> sudo apt-get install python-pip
   >> sudo python setup.py install

14、安装dpark
::

   >> sudo apt-get install git libzmq-dev python-pip python-dev
   >> git clone https://github.com/douban/dpark.git
   >> cd dpark
   >> sudo apt-get install python-psutil psutils
   >> sudo python setup.py install

15、修改/etc/hosts
::

   >> sudo emacs /etc/hosts
   192.168.1.201    pc1
   192.168.1.202    pc2
   192.168.1.203    pc3
   192.168.1.204    pc4
   192.168.1.211    cn001
   192.168.1.212    cn002
   192.168.1.213    cn003
   192.168.1.214    cn004
   192.168.1.215    cn005
   192.168.1.216    cn006
   192.168.1.217    cn007
   192.168.1.218    cn008
   192.168.1.219    cn009
   192.168.1.220    cn010
   192.168.1.221    cn011
   192.168.1.222    cn012
   192.168.1.241    snc001
   192.168.1.242    snc002
   192.168.1.243    snc003
   192.168.1.244    snc004
   192.168.1.210    client

16、配置SSH无密码登录
::

   >> ssh-keygen -t rsa -P ''
   >> cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
   >> sudo chmod 600 ~/.ssh/authorized_keys
