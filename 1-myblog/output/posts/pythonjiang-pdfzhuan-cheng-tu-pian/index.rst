.. title: Python将PDF转成图片
.. slug: pythonjiang-pdfzhuan-cheng-tu-pian
.. date: 2018-01-28 21:10:52 UTC+08:00
.. tags: PDF, PNG
.. category: Python
.. link: 
.. description: 
.. type: text


使用Python的fitz库，参考代码：


.. code-block :: python
    :linenos:

    import fitz

    sizelist = [5, 5.5, 6.5, 7.5, 8, 9,
                10, 10.5, 12, 14, 16, 18,
                20, 22, 24, 26, 28, 36,
                42, 48, 60, 72]

    for si in sizelist:
        print(si)
        docs = fitz.open("字库/"+str(si)+"/字库.pdf")
        pagenum = 1
        for i in range(0, docs.pageCount):
            page = docs.getPagePixmap(i)
            page.writePNG("textdb/"+str(si)+"/page" + str(pagenum)+".png")
            pagenum = pagenum + 1

