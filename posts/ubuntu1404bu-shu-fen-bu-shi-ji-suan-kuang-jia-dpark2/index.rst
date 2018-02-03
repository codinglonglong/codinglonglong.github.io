.. title: Ubuntu14.04部署分布式计算框架Dpark（2）
.. slug: ubuntu1404bu-shu-fen-bu-shi-ji-suan-kuang-jia-dpark2
.. date: 2015-09-16 04:27:14 UTC+08:00
.. tags: 分布式, Ubuntu14.04部署分布式计算框架Dpark, Dpark, Moosefs, Beansdb, Mesos, kvm
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

**在pc1上**

1、安装KVM，参考文章 https://codinglonglong.github.io/posts/ubuntuan-zhuang-kvmxu-ni-ji/

2、配置KVM桥接
::

   >> sudo apt-get install uml-utilities
   >> sudo emacs /etc/network/interfaces
   auto eth0
   iface eth0 inet manual

   auto tap0
   iface tap0 inet manual
   up ifconfig $IFACE 0.0.0.0 up
   down ifconfig $IFACE down
   tunctl_user long

   auto br0
   iface br0 inet static
   bridge_ports eth0 tap0
   address 192.168.1.201
   netmask 255.255.255.0
   network 192.168.1.0
   broadcast 192.168.1.255
   gateway 192.168.1.1 
   dns-nameserver 202.98.198.167

3、删除virbr0，参考文章 https://codinglonglong.github.io/posts/kvmshan-chu-virbr0/

4、重启系统

5、启动virt-manager，安装计算节点cn001，使用Ubuntu Server 14.04.3系统，1个CPU，2G内存，10G硬盘。

