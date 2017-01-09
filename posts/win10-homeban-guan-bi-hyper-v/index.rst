.. title: Win10 home版关闭hyper-v
.. slug: win10-homeban-guan-bi-hyper-v
.. date: 2017-01-10 04:45:37 UTC+08:00
.. tags: win10, hyper-v, Android, haxm
.. category: Android
.. link: 
.. description: 
.. type: text

在win10的home版中，安装Android Studio提供的haxm，会出现死机的现象，这是由于haxm与hyper-v冲突。而home版无法通过“启用或关闭Windows功能”来关闭hyper-v。这时可以通过如下方法关闭hyper-v。

1. 管理员身份运行命令提示符cmd

    .. code-block:: bash

        >> bcdedit /copy {current} /d "Windows10 no Hyper-V
        >> bcdedit /set {XXX} hypervisorlaunchtype OFF

   注意XXX的部分是上一步的输出结果。

2. 重启Win10，选择“Windows10 no Hyper-V”，即可进入没有Hyper-V的win10系统。

**注意** 

如果要安装haxm，还需要注意以下两点：

1. 别忘了在BIOS里打开虚拟化。
2. haxm不仅会与hyper-v冲突，与杀毒软件Avast也会冲突，安装haxm之前先卸载掉Avast才行。

