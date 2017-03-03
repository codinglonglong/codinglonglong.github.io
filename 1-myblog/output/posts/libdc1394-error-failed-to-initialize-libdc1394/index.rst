.. title: libdc1394 error: Failed to initialize libdc1394
.. slug: libdc1394-error-failed-to-initialize-libdc1394
.. date: 2017-03-03 19:22:25 UTC+08:00
.. tags: Linux
.. category: Linux
.. link: 
.. description: 
.. type: text

在使用pydecodeqr时，出现了如下错误信息：

    ::

        libdc1394 error: Failed to initialize libdc1394

可以通过如下方法解决：

    ::

        >> sudo ln /dev/null /dev/raw1394

        