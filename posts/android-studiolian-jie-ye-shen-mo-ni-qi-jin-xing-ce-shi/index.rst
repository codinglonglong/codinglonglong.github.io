.. title: Android Studio连接夜神模拟器进行测试
.. slug: android-studiolian-jie-ye-shen-mo-ni-qi-jin-xing-ce-shi
.. date: 2017-05-14 14:40:57 UTC+08:00
.. tags: Android, 夜神模拟器
.. category: Android
.. link: 
.. description: 
.. type: text

在之前的文章 https://codinglonglong.github.io/posts/android-studiolian-jie-droid4xdiao-shi-app/ 中，我们已经成功使用Droid4X进行APP开发测试，这次我们使用夜神模拟器完成同样的工作。

1. 安装夜神模拟器。

2. 添加夜神模拟器的可执行路径到系统路径，我的在

    .. code-block:: bash
    
        C:\Program Files\nox\Nox\bin

3. 启动夜神模拟器服务。

    .. code-block:: bash
    
        >> nox_adb.exe connect 127.0.0.1:62001

   出现

    .. code-block:: bash

       * daemon started successfully *
        connected to 127.0.0.1:62001

4. 在Android Studio中启动调试即可。

