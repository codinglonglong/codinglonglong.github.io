.. title: Ubuntu14.04部署分布式计算框架Dpark（3）
.. slug: ubuntu1404bu-shu-fen-bu-shi-ji-suan-kuang-jia-dpark3
.. date: 2015-09-16 05:08:52 UTC+08:00
.. tags: 分布式, Ubuntu14.04部署分布式计算框架Dpark, Dpark, Moosefs, Beansdb, Mesos, kvm
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

**在cn001上**

1、安装ssh和emacs
::

   >> sudo apt-get update
   >> sudo apt-get install ssh openssh-server openssh-client emacs

2、设定静态IP，参考文章 https://codinglonglong.github.io/posts/ubuntu1404bu-shu-tornado%2Bnginx%2Bsupervisor/

3、重启系统

4、安装Beansdb的Python接口
::

   >> cd ~
   >> sudo apt-get install build-essential gcc g++ gfortran git python-pip python-dev autoconf automake libtool 
   >> scp long@192.168.1.203:/home/long/libmemcached-1.0.18.tar.gz .
   >> tar zxvf libmemcached-1.0.18.tar.gz
   >> cd libmemcached-1.0.18/
   >> ./configure
   >> sudo make
   >> sudo make install
   >> git clone https://github.com/douban/python-libmemcached
   >> cd python-libmemcached/
   >> sudo python setup.py install
   >> emacs ~/.profile
   export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
   >> source ~/.profile
   >> sudo scp long@192.168.1.203:/home/long/beansdb/python/dbclient.py /usr/local/lib/python2.7/dist-packages/

5、安装MooseFS的客户端
::

   >> cd ~
   >> scp long@192.168.1.203:/home/long/fuse-2.9.4.tar.gz .
   >> scp long@192.168.1.203:/home/long/zlib-1.2.8.tar.gz .
   >> scp long@192.168.1.203:/home/long/moosefs-2.0.73-1.tar.gz .
   >> tar zxvf fuse-2.9.4.tar.gz && cd fuse-2.9.4 && ./configure --prefix=/usr && sudo make && sudo make install && cd ..
   >> tar zxvf zlib-1.2.8.tar.gz && cd zlib-1.2.8 && ./configure && sudo make && sudo make install && cd ..
   >> sudo useradd mfs -M -s /sbin/nologin
   >> sudo apt-get install libpcap-dev pkg-config
   >> tar zxvf moosefs-2.0.73-1.tar.gz && cd moosefs-2.0.73 && ./configure --prefix=/usr/local/mfs --with-default-user=mfs --with-default-group=mfs --enable-mfsmount && sudo make && sudo make install && cd ..
   >> cd /usr/local/mfs/etc/mfs
   >> sudo cp mfsmount.cfg.dist mfsmount.cfg
   >> sudo emacs mfsmount.cfg
   # Example:
   #
   /mnt/mfs
   >> sudo mkdir /mnt/mfs
   >> sudo chown -R mfs:mfs /mnt/mfs

6、建立自启动脚本
::

   >> cd /usr/local/bin
   >> sudo emacs startmfsmount
   cd /usr/local/mfs/bin/
   ./mfsmount -H 192.168.1.203 -o nonempty
   >> sudo chmod 777 startmfsmount

7、设定无密码启动
::

   >> sudo visudo
   long ALL=NOPASSWD:/usr/local/bin/startmfsmount

8、安装Mesos的客户端
::

   >> scp -r long@192.168.1.203:/home/long/mesos /home/long
   >> sudo apt-get install build-essential openjdk-6-jdk python-dev python-boto libcurl4-nss-dev libsasl2-dev maven libapr1-dev libsvn-dev autoconf libtool

9、建立自启动脚本
::

   >> cd /usr/local/bin
   >> sudo emacs startmesosslave
   cd /home/long/mesos/sbin
   ./mesos-slave --master=192.168.1.203:5050 --quiet &
   >> sudo chmod 777 startmesosslave

10、设定无密码启动
::

   >> sudo visudo
   long ALL=NOPASSWD:/usr/local/bin/startmesosslave

11、安装Pymesos
::

   >> git clone https://github.com/douban/pymesos.git
   >> cd pymesos
   >> sudo apt-get install python-pip
   >> sudo python setup.py install

12、安装Dpark
::

   >> sudo apt-get install git libzmq-dev python-pip python-dev
   >> git clone https://github.com/douban/dpark.git
   >> cd dpark
   >> sudo apt-get install python-psutil psutils
   >> sudo python setup.py install

13、配置ssh无密码登录
::

   >> scp long@192.168.1.203:/home/long/.ssh/authorized_keys ~/.ssh/
   >> sudo chmod 600 ~/.ssh/authorized_keys

14、修改/etc/hosts
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

15、测试Beansdb
::

   >> sudo emacs dbtest.py
   from dbclient import Beansdb

   BEANSDBCFG = {
       "192.168.1.203:7900": range(16)
   }

   db = Beansdb(BEANSDBCFG, 16)
   for x in range(1, 10):
       db.set(str(x), str(x**2))
   for x in range(1, 10):
       print(db.get(str(x)))
   >> python dbtest.py
   >> 1
   >> 4
   >> 9
   >> 16
   >> 25
   >> 36
   >> 49
   >> 64
   >> 81

16、测试Dpark
::

   >> emacs dparktest.py
   import time
   start = time.clock()
   
   from dpark import DparkContext
   from random import random
   dpk = DparkContext()
   count = dpk.accumulator(0)


   def random_once(*args, **kwrgs):
       x = random() * 2 - 1
       y = random() * 2 - 1
       if x * x + y * y < 1:
           count.add(1)

   N = 100000
   
   dpk.parallelize(range(0, N), 50).foreach(random_once)
   print("PI is roughly: " + str(4.0 * count.value / N))
   
   end = time.clock()
   print(end - start)
   >> python dparktest.py
   >> python dparktest.py -m mesos://192.168.1.203:5050

17、测试MooseFS
::

   >> emacs mfstest.py
   from dpark import DparkContext
   dpk = DparkContext()
   f = dpk.textFile("/mnt/mfs/lastfm-dataset-1K/userid-profile.tsv")
   print(f.count())
   >> python mfstest.py -m mesos://192.168.1.203:5050

