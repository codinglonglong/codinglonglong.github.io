.. title: Python3向SQLite写入图片
.. slug: python3xiang-sqlitexie-ru-tu-pian
.. date: 2015-09-07 12:36:21 UTC+08:00
.. tags: Python, 图片处理
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

**使用Python3向SQLite写入图片。**

看代码binaryread.py：

.. code-block :: python
    :linenos:

    import sqlite3

    with open("test.jpg", "rb") as fp:
        picbin = fp.read()
    
    cont = sqlite3.connect("temp.db")
    cur = cont.cursor()
    sql = """create table pic(pic blob)"""
    cur.execute(sql)
    sql = """insert into pic(pic) values(?)"""
    b = sqlite3.Binary(picbin)
    cur.execute(sql, (b,))
    cont.commit()

执行代码，程序读取当前目录下的test.jpg，写入一个新创建的数据库，文件名是temp.db。

然后读取图片数据，写入一个新的文件，看代码binarywrite.py：

.. code-block :: python
    :linenos:

    import sqlite3

    cont = sqlite3.connect("temp.db")
    cur = cont.cursor()
    sql = """select pic from pic"""
    cur.execute(sql)
    pic = cur.fetchone()[0]
    with open("test1.jpg", "wb") as fp:
        fp.write(pic)

执行代码，生成了一个和test.jpg内容完全一样的test1.jpg。

综上，在涉及到二进制数据写入SQLite数据库时，要使用sqlite3.Binary将二进制转换成SQLite可以写入的参数类型。
