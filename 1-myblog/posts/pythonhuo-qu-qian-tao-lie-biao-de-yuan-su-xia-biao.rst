.. title: Python获取嵌套列表的元素下标
.. slug: pythonhuo-qu-qian-tao-lie-biao-de-yuan-su-xia-biao
.. date: 2015-09-07 12:25:33 UTC+08:00
.. tags: 算法, Python
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

**题目可以描述为：**

已经定义如下列表：

.. code-block :: python
    :linenos:

    lista = [1, 8, [4, 5, 8, 5, 8, 7, 6], [3, [10, 8, 11, [12, 13, 8], 8]], 8]

求元素8在嵌套列表lista中的下标。

解决方法——递归：

.. code-block :: python
    :linenos:

    lista = [1, 8, [4, 5, 8, 5, 8, 7, 6], [3, [10, 8, 11, [12, 13, 8], 8]], 8]


    def judge_find(templist, pathlist, x):
        for i in pathlist:
            templist = templist[i]
            if templist == x:
                return True
        else:
            return False


    def find_multiple_index(originlist, templist, x, pathlist, resultlist):
        for i in range(len(templist)):
            if templist[i] == x:
                pathlist.append(i)
                resultlist.append(tuple(pathlist[:]))
                pathlist.pop()
            else:  
                if type(templist[i]) is list:
                    pathlist.append(i)
                    if not find_multiple_index(originlist, templist[i], x, pathlist, resultlist):
                        if len(pathlist) != 0:
                            pathlist.pop()

    pathlist = []
    resultlist = []
    find_multiple_index(lista[:], lista, 8, pathlist, resultlist)
    print(resultlist)

运行结果：

::

   >> long@mylife:~/Downloads$ python3 tree_find_any_position.py 
   >> [(1,), (2, 2), (2, 4), (3, 1, 1), (3, 1, 3, 2), (3, 1, 4), (4,)]

