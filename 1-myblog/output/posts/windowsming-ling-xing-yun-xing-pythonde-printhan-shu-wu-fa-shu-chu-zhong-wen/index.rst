.. title: Windows命令行运行Python的print函数无法输出中文
.. slug: windowsming-ling-xing-yun-xing-pythonde-printhan-shu-wu-fa-shu-chu-zhong-wen
.. date: 2017-04-02 21:54:15 UTC+08:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

代码中加入如下内容：

    .. code-block:: python
        :number-lines:

        import io
        import sys
        sys.stdout = io.TextIOWrapper(sys.stdout.buffer,encoding='utf-8')

    