.. title: Exception in thread "main" java.util.zip.ZipException: error in opening zip file
.. slug: exception-in-thread-main-javautilzipzipexception-error-in-opening-zip-file
.. date: 2017-01-10 22:59:06 UTC+08:00
.. tags: react-native, react
.. category: react
.. link: 
.. description: 
.. type: text

在参考 https://reactnative.cn/docs/0.40/getting-started.html 配置react-native的过程中，发生了如下错误：

.. code-block:: bash

    Starting JS server...
        Building and installing the app on the device (cd android && ./gradlew installDebug)...
        Unzipping /home/long/.gradle/wrapper/dists/gradle-2.4-all/6r4uqcc6ovnq6ac6s0txzcpc0/gradle-2.4-all.zip to /home/long/.gradle/wrapper/dists/gradle-2.4-all/6r4uqcc6ovnq6ac6s0txzcpc0
        Exception in thread "main" java.util.zip.ZipException: error in opening zip file
            at java.util.zip.ZipFile.open(Native Method)
            at java.util.zip.ZipFile.<init>(ZipFile.java:219)
            at java.util.zip.ZipFile.<init>(ZipFile.java:149)
            at java.util.zip.ZipFile.<init>(ZipFile.java:163)
            at org.gradle.wrapper.Install.unzip(Install.java:159)
            at org.gradle.wrapper.Install.access$500(Install.java:26)
            at org.gradle.wrapper.Install$1.call(Install.java:69)
            at org.gradle.wrapper.Install$1.call(Install.java:46)
            at org.gradle.wrapper.ExclusiveFileAccessManager.access(ExclusiveFileAccessManager.java:65)
            at org.gradle.wrapper.Install.createDist(Install.java:46)
            at org.gradle.wrapper.WrapperExecutor.execute(WrapperExecutor.java:126)
            at org.gradle.wrapper.GradleWrapperMain.main(GradleWrapperMain.java:61)
    Could not install the app on the device, read the error above for details.
    Make sure you have an Android emulator running or a device connected and have
    set up your Android development environment:
    https://facebook.github.io/react-native/docs/android-setup.html

解决方法：

从 https://services.gradle.org/distributions 下载完整的gradle-2.4-all.zip文件，放到 C:\\Users\\long\\.gradle\\wrapper\\dists\\gradle-2.4-all\\6r4uqcc6ovnq6ac6s0txzcpc0 目录中即可正常运行 react-native run-android。

放张成功之后的截图：

.. image:: https://github.com/longlongpicture/myblogpicture/raw/master/react-native-1.PNG

