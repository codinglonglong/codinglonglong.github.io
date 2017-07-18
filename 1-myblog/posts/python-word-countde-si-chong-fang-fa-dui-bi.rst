.. title: Python Word Count的四种方法对比
.. slug: python-word-countde-si-chong-fang-fa-dui-bi
.. date: 2015-09-09 10:52:56 UTC+08:00
.. tags: Python, map, reduce, 多线程, 多进程
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

Word Count可以认为是大数据时代的Hello World。我们使用Python按照四种方案进行一篇文章的词数统计，并进行性能对比，我们已经手工去除了乱码和多余的标点。

方案1、内置map和reduce函数

.. code-block :: python
    :linenos:

    # 内置map和reduce函数
    print("内置map和reduce函数")
    import time
    start = time.clock()

    from functools import reduce
    with open("sample.txt", "r") as fp:
        # 读取文件
        datas = fp.readlines()
        # 使用mapreduce统计单词数目
        wordcount = reduce(lambda x, y: x + y,
                           map(lambda x: len(x.split()), datas))
        print(wordcount)

    end = time.clock()
    print(end - start)


运行结果：
    
.. code-block :: python 
    :linenos:

    >> 内置map和reduce函数
    >> 767
    >> 0.008342000000000002

方案2、直接计算单词个数

.. code-block :: python 
    :linenos:

    # 直接计算单词个数
    print("直接计算单词个数")
    import time
    start = time.clock()

    with open("sample.txt", "r") as fp:
        # 读取文件
        datas = fp.readlines()
        # 合并成一个字符串
        datas = " ".join(datas)
        # 划分成单词
        datas = datas.split()
        # 求单词数目
        wordcount = len(datas)
        print(wordcount)

    end = time.clock()
    print(end - start)


运行结果：

.. code-block :: python 
    :linenos:

    >> 直接计算单词个数
    >> 767
    >> 0.0002339999999999981


方案3、多线程MapReduce

.. code-block :: python 
    :linenos:

    # 多线程MapReduce
    print("多线程MapReduce")
    import time
    start = time.clock()
    
    import threading
    from queue import Queue
    from functools import reduce


    class WordCount(threading.Thread):
        def __init__(self, wordstr, queue):
            threading.Thread.__init__(self)
            self.queue = queue
            self.wordstr = wordstr

        def run(self):
            self.queue.put(len(self.wordstr.split()))


    with open("sample.txt", "r") as fp:
        datas = fp.readlines()
        threadlist = []
        queue = Queue()
        for x in datas:
            threadlist.append(WordCount(x, queue))
        for trd in threadlist:
            trd.start()
        for trd in threadlist:
            trd.join()
        datalist = [queue.get() for x in range(queue.qsize())]
        wordcount = reduce(lambda x, y: x + y, datalist)
        print(wordcount)

    end = time.clock()
    print(end - start)

注意：Python提供的Queue是线程安全的，所以这里不需要锁。
    
运行结果：

.. code-block :: python 
    :linenos:

    >> 多线程MapReduce
    >> 767
    >> 0.02518399999999999


方案4、多进程MapReduce

.. code-block :: python 
    :linenos:

    # 多进程MapReduce
    print("多进程MapReduce")
    import time
    start = time.clock()

    from multiprocessing import Pool
    from functools import reduce


    def wordcount(wordstr):
        return len(wordstr.split())


    with open("sample.txt", "r") as fp:
        datas = fp.readlines()
        p = Pool()
        datalist = p.map(wordcount, datas)
        wordcount = reduce(lambda x, y: x + y, datalist)
        print(wordcount)

    end = time.clock()
    print(end - start)

注意：Python提供的进程池Pool自带map函数。
   
运行结果：

.. code-block :: python 
    :linenos:

    >> 多进程MapReduce
    >> 767
    >> 0.056589


性能对比十分明显：
直接计算单词个数 > 内置map和reduce函数 > 多线程MapReduce > 多进程MapReduce

可见，在单机运行环境中，MapReduce不能起到提高性能的作用。
