.. title: 安装Deepin和RemixOS双系统
.. slug: an-zhuang-deepinhe-remixosshuang-xi-tong
.. date: 2017-05-21 12:08:11 UTC+08:00
.. tags: Deepin, RemixOS
.. category: Linux
.. link: 
.. description: 
.. type: text


RemixOS是PC版的Android，可以运行一部分Android应用。

RemixOS下载地址： https://sourceforge.net/projects/remix-os/

1、在Windows上，下载RemixOS安装包，解压缩，用Remix_OS_for_PC_Installation_Tool制作RemixOS安装U盘。

2、将安装U盘插入Deepin所在的笔记本（基于Ubuntu的发行版同理）。

3、启动Deepin，在根目录下创建文件夹Remix（这里需要管理员权限）。

4、在Remix中创建目录DATA（用来存放数据）。

5、把U盘上的内容全部拷贝到Remix目录中。

6、修改引导文件。

    .. code-block:: bash

        >> sudo gedit /etc/grub.d/40_custom
        #!/bin/sh
        exec tail -n +3 $0
        # This file provides an easy way to add custom menu entries.  Simply type the
        # menu entries you want to add after this comment.  Be careful not to change
        # the 'exec tail' line above.
        menuentry 'Remix OS For PC' --class android-x86{
            set root=(hd0,3)
            linux /Remix/kernel root=/dev/sda3/Remix androidboot.hardware=remix_cn_x86_64 androidboot.selinux=permissive quiet DATA=/Remix/DATA SRC=/Remix nomodeset
            initrd /Remix/initrd.img
        }
        >> sudo grub-install 40_custom
        >> sudo update-grub
        >> sudo reboot


经过反复试验，RemixOS总是卡在开机的Logo画面上，两年前，我在同一个笔记本上安装RemixOS时是正常进入系统的。这次放了两个小时都没有进去，也没有任何提示信息……目前估计是系统镜像的问题，网上提到同样问题的人也很多……当前系统的版本是B2016112101。

如果有哪位大神解决了这个问题，可以顺便告诉我一下，非常感谢。

联系方式在“联系我” https://codinglonglong.github.io/posts/lian-xi-wo/ 页面中。


**注意**

1、(hd0,3)指的是第0号硬盘的第3号分区。

2、引导文件不要轻易加空格。

