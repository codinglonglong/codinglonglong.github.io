.. title: KVM克隆虚拟机
.. slug: kvmke-long-xu-ni-ji
.. date: 2015-09-16 15:15:30 UTC+08:00
.. tags: kvm, 分布式
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

1、启动virt-manager，右击cn001，点击"Clone..."，在弹出窗口的Name中输入"cn002"，点击"Clone"。

2、克隆完成后，启动cn002。

3、修改hostname
::

   >> sudo emacs /etc/hostname
   cn002

4、修改IP地址
::

   >> sudo emacs /etc/network/interfaces
   address 192.168.1.212

5、重启就可以正常使用cn002了。
