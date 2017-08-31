.. title: Ubuntu修改启动动画
.. slug: ubuntuxiu-gai-qi-dong-dong-hua
.. date: 2015-09-07 10:26:38 UTC+08:00
.. tags: Ubuntu
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

1、安装启动动画
::

   >> long@happytime:~$ sudo apt-get install plymouth-theme-*

2、修改默认启动动画
::

   >> long@happytime:~$ sudo update-alternatives --config default.plymouth

执行之后可以得到所有可用的启动动画，如下：
::

   >> 有 15 个候选项可用于替换 default.plymouth (提供 /lib/plymouth/themes/default.plymouth)。
   >>  选择       路径                                                             优先级  状态
   >> ------------------------------------------------------------
   >>   0            /lib/plymouth/themes/edubuntu-logo/edubuntu-logo.plymouth           150       自动模式
   >>   1            /lib/plymouth/themes/edubuntu-logo/edubuntu-logo.plymouth           150       手动模式
   >>   2            /lib/plymouth/themes/fade-in/fade-in.plymouth                       10        手动模式
   >>   3            /lib/plymouth/themes/glow/glow.plymouth                             10        手动模式
   >>   4            /lib/plymouth/themes/kubuntu-logo/kubuntu-logo.plymouth             150       手动模式
   >>   5            /lib/plymouth/themes/lubuntu-logo/lubuntu-logo.plymouth             150       手动模式
   >>   6            /lib/plymouth/themes/numix/numix.plymouth                           100       手动模式
   >>   7            /lib/plymouth/themes/sabily/sabily.plymouth                         60        手动模式
   >>   8            /lib/plymouth/themes/script/script.plymouth                         10        手动模式
   >> * 9            /lib/plymouth/themes/solar/solar.plymouth                           10        手动模式
   >>   10           /lib/plymouth/themes/spinfinity/spinfinity.plymouth                 10        手动模式
   >>   11           /lib/plymouth/themes/ubuntu-gnome-logo/ubuntu-gnome-logo.plymouth   150       手动模式
   >>   12           /lib/plymouth/themes/ubuntu-logo/ubuntu-logo-scale-2.plymouth       99        手动模式
   >>   13           /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth               100       手动模式
   >>   14           /lib/plymouth/themes/ubuntustudio-logo/ubuntustudio-logo.plymouth   150       手动模式
   >>   15           /lib/plymouth/themes/xubuntu-logo/xubuntu-logo.plymouth             150       手动模式
   >> 
   >> 要维持当前值[*]请按回车键，或者键入选择的编号：
   
3、输入编号
::

   >> 要维持当前值[*]请按回车键，或者键入选择的编号：10
   >> update-alternatives: using /lib/plymouth/themes/spinfinity/spinfinity.plymouth to provide /lib/plymouth/themes/default.plymouth (default.plymouth) in 手动模式

4、更新设置
::

   >> sudo update-initramfs -u

重启即可看到切换之后的启动画面。
