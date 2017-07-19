.. title: Ubuntu安装KVM虚拟机
.. slug: ubuntuan-zhuang-kvmxu-ni-ji
.. date: 2015-09-07 19:19:08 UTC+08:00
.. tags: kvm, Ubuntu
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

1、检查CPU是否支持虚拟化。
::

   >> long@mylife:~$ egrep -o '(vmx|svm)' /proc/cpuinfo
   >> vmx
   >> vmx
   >> vmx
   >> vmx

2、安装KVM相关软件
::

   >> sudo apt-get install qemu-kvm libvirt-bin virt-manager bridge-utils

3、检查安装状态
::

   >> long@mylife:~$ lsmod | grep kvm
   >> kvm_intel             143630  0 
   >> kvm                   452096  1 kvm_intel

4、启动虚拟系统管理器
::

   >> virt-manager

5、提示安装新的软件包，选择“是”==>“安装"==>"继续"

6、提示无法连接到libvirt，重启

7、启动虚拟系统管理器，至此KVM安装完成
