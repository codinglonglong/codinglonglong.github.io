.. title: Python实现Excel列名和下标的相互转换
.. slug: pythonshi-xian-excellie-ming-he-xia-biao-de-xiang-hu-zhuan-huan
.. date: 2017-12-12 00:17:58 UTC+08:00
.. tags: Python, Excel
.. category: Python
.. link: 
.. description: 
.. type: text


.. code-block:: python
    :number-lines:

    def getcolnum(colname):
        """
        列名转下标，0起
        :param colname:列名
        :return:下标
        """
        thesum = 0
        length = len(colname)
        loop = length - 1
        while loop >= 0:
            thesum = thesum + (ord(colname[length - loop - 1]) - ord('A') + 1) * (26 ** loop)
            loop = loop - 1
        return thesum - 1


    def colnumgenerator():
        sourcevalue = 1
        while True:
            valuestr = ""
            remainlist = []
            value = sourcevalue
            while value:
                remain = value % 26
                value = value // 26
                if remain == 0:
                    remainlist.append(26)
                    value = value - 1
                else:
                    remainlist.append(remain)
            remainlist.reverse()
            for rem in remainlist:
                valuestr = valuestr + chr(ord('A') + rem - 1)
            sourcevalue = sourcevalue + 1
            yield valuestr


    def getcolname(colnum):
        """
        下标转列名，0起
        :param colnum:下标
        :return:列名
        """
        count = 0
        for i in colnumgenerator():
            count = count + 1
            if count == colnum + 1:
                return i

    