.. title: KVM删除virbr0
.. slug: kvmshan-chu-virbr0
.. date: 2015-09-10 18:30:08 UTC+08:00
.. tags: kvm, 桥接, 分布式
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

安装KVM后，通过ifconfig，看到了一个名为virbr0的虚拟网络接口。

由于在实验中，我们采用桥接方式使用虚拟机，所以这个接口是没有用的，我们通过如下方法可以将其删除。

::

   >> virsh net-list
   >> virsh net-destroy default  #这里的default是上一步输出结果中的。
   >> virsh net-undefine default
   >> sudo service libvirt-bin restart

重启系统即可。
