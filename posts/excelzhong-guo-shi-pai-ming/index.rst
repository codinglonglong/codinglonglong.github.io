.. title: Excel中国式排名
.. slug: excelzhong-guo-shi-pai-ming
.. date: 2018-01-29 09:28:24 UTC+08:00
.. tags: Excel
.. category: win10
.. link: 
.. description: 
.. type: text


假设Y5是数据的第一行，Y5:Y45是所有数据，那么在排名列的第一行输入

::
    
    =RANK(Y5,$Y$5:$Y$45,0)

向下填充之后就实现中国式排名了。


