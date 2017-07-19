.. title: Ubuntu查看硬件配置
.. slug: ubuntucha-kan-ying-jian-pei-zhi
.. date: 2015-09-07 19:12:33 UTC+08:00
.. tags: Ubuntu, 硬件配置
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

1. 查看系统内核
::

    >> long@pc1:/proc$ uname -a
    >> Linux pc1 3.16.0-41-generic #55~14.04.1-Ubuntu SMP Sun Jun 14 18:43:36 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

2. 查看CPU
::

    >> long@pc1:/proc$ cat /proc/cpuinfo | grep model\ name
    >> model name	: Pentium(R) Dual-Core  CPU      E5500  @ 2.80GHz
    >> model name	: Pentium(R) Dual-Core  CPU      E5500  @ 2.80GHz

3. 查看内存
::

    >> long@pc1:/proc$ cat /proc/meminfo | grep MemTotal
    >> MemTotal:        4012620 kB

4. 查看显卡
::

    >> long@pc1:/proc$ lspci | grep 'VGA'
    >> 00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

5. 查看声卡
::

    >> long@pc1:/proc$ lspci | grep -i 'Audio'
    >> 00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)

6. 查看网卡
::

    >> long@pc1:/proc$ lspci | grep -i 'Ethernet'
    >> 02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller (rev 10)

7. 查看硬盘
::

    >> long@pc1:/proc$ df -lh
    >> Filesystem      Size  Used Avail Use% Mounted on
    >> /dev/sda1       292G  4.2G  273G   2% /
    >> none            4.0K     0  4.0K   0% /sys/fs/cgroup
    >> udev            2.0G  4.0K  2.0G   1% /dev
    >> tmpfs           392M  1.1M  391M   1% /run
    >> none            5.0M     0  5.0M   0% /run/lock
    >> none            2.0G   76K  2.0G   1% /run/shm
    >> none            100M   32K  100M   1% /run/user
