.. title: Python判断字符串中是否含有中文
.. slug: pythonpan-duan-zi-fu-chuan-zhong-shi-fou-han-you-zhong-wen
.. date: 2017-07-12 19:37:44 UTC+08:00
.. tags: Python
.. category: Python 
.. link: 
.. description: 
.. type: text


.. code-block:: python
    :number-lines:

    def haschinese(text):
        for t in text:
            if '\u4e00' <= t <= '\u9fff':
                return True
        return False

