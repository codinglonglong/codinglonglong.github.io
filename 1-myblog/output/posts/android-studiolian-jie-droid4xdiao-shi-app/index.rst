.. title: Android Studio连接Droid4X调试APP
.. slug: android-studiolian-jie-droid4xdiao-shi-app
.. date: 2017-01-10 04:32:37 UTC+08:00
.. tags: Android, Droid4X
.. category: Android
.. link: 
.. description: 
.. type: text

Android Studio用内置的虚拟机连i7的本都要跑半天，外接手机的话又太费手机，所以我们可以采用第三方Android虚拟机的方式来调试程序，在这里我们使用的是Droid4X。

1. 安装VirtualBox。
2. 安装Droid4X。
3. 添加adb到系统路径，我的在

    .. code-block:: bash
    
        C:\Users\long\AppData\Local\Android\sdk\platform-tools

4. 连接adb到Droid4X。

    .. code-block:: bash
    
        >> adb connect 127.0.0.1:26944

   出现

    .. code-block:: bash

       * daemon started successfully * 

5. 启动调试即可。

