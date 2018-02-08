.. title: 修改Docker中的系统时间
.. slug: xiu-gai-dockerzhong-de-xi-tong-shi-jian
.. date: 2017-01-31 15:36:34 UTC+08:00
.. tags: Docker, Linux
.. category: Linux
.. link: 
.. description: 
.. type: text

默认在Docker中无法使用常见的命令修改系统时间，会显示没有权限，但测试程序往往需要修改系统时间，可以通过如下方法解决该问题：

        .. code-block:: bash

            root@d26965edacdd:/# TZ=Etc/GMT
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 07:39:26 GMT 2017
            root@d26965edacdd:/# TZ=Etc/GMT-1
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 08:39:35 +01 2017
            root@d26965edacdd:/# TZ=Etc/GMT-2
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 09:39:40 +02 2017
            root@d26965edacdd:/# TZ=Etc/GMT-3
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 10:39:45 +03 2017
            root@d26965edacdd:/# TZ=Etc/GMT-4
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 11:42:57 +04 2017
            root@d26965edacdd:/# TZ=Etc/GMT-5
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 12:43:05 +05 2017
            root@d26965edacdd:/# TZ=Etc/GMT-6
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 13:43:10 +06 2017
            root@d26965edacdd:/# TZ=Etc/GMT-7
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 14:43:15 +07 2017
            root@d26965edacdd:/# TZ=Etc/GMT-8
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 15:43:20 +08 2017
            root@d26965edacdd:/# TZ=Etc/GMT-9
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 16:43:25 +09 2017
            root@d26965edacdd:/# TZ=Etc/GMT-10
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 17:43:30 +10 2017
            root@d26965edacdd:/# TZ=Etc/GMT-11
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 18:43:35 +11 2017
            root@d26965edacdd:/# TZ=Etc/GMT-12
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 19:43:39 +12 2017
            root@d26965edacdd:/# TZ=Etc/GMT-13
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 20:43:43 +13 2017
            root@d26965edacdd:/# TZ=Etc/GMT-14
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 21:43:50 +14 2017

            root@d26965edacdd:/# TZ=Etc/GMT+1
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 06:44:57 -01 2017
            root@d26965edacdd:/# TZ=Etc/GMT+2
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 05:45:01 -02 2017
            root@d26965edacdd:/# TZ=Etc/GMT+3
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 04:45:05 -03 2017
            root@d26965edacdd:/# TZ=Etc/GMT+4
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 03:45:09 -04 2017
            root@d26965edacdd:/# TZ=Etc/GMT+5
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 02:45:13 -05 2017
            root@d26965edacdd:/# TZ=Etc/GMT+6
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 01:45:17 -06 2017
            root@d26965edacdd:/# TZ=Etc/GMT+7
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Tue Jan 31 00:45:24 -07 2017
            root@d26965edacdd:/# TZ=Etc/GMT+8
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Mon Jan 30 23:45:28 -08 2017
            root@d26965edacdd:/# TZ=Etc/GMT+9
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Mon Jan 30 22:45:32 -09 2017
            root@d26965edacdd:/# TZ=Etc/GMT+10
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Mon Jan 30 21:45:37 -10 2017
            root@d26965edacdd:/# TZ=Etc/GMT+11
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Mon Jan 30 20:45:53 -11 2017
            root@d26965edacdd:/# TZ=Etc/GMT+12
            root@d26965edacdd:/# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/# date
            Mon Jan 30 19:46:00 -12 2017

我们测试一下实际效果：

        .. code-block:: bash

            root@d26965edacdd:/usr/development# cat test.py
            import time
            print(time.strftime('%Y-%m-%d %H:%M:%S',time.localtime(time.time())))
            root@d26965edacdd:/usr/development# TZ=Etc/GMT
            root@d26965edacdd:/usr/development# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/usr/development# python test.py
            2017-01-31 07:50:13
            root@d26965edacdd:/usr/development# TZ=Etc/GMT-8
            root@d26965edacdd:/usr/development# ln -snf /usr/share/zoneinfo/$TZ /etc/localtime  && echo $TZ > /etc/timezone
            root@d26965edacdd:/usr/development# python test.py
            2017-01-31 15:50:19


**注意** 

本方法是通过修改时区来“曲线救国”的。

