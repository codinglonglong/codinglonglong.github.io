.. title: Java代码案例27——分支判断是否做核酸
.. slug: javadai-ma-an-li-27-fen-zhi-pan-duan-shi-fou-zuo-he-suan
.. date: 2022-11-14 23:20:51 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text


.. code-block:: java
    :number-lines:

// Java分支判断是否做核酸，用或者||连接多个条件
// 每周一、四、六常态化核酸
package xiangmu;

public class Ceshi {
    public static void main(String args[]) {
        int xingqi = 6;
        if(xingqi == 1 || xingqi == 4 || xingqi == 6) {
        	dayin("今天做核酸");
        }else {
        	dayin("今天不做核酸");
        }
    }
    public static void dayin(String zifuchuan) {
        System.out.println(zifuchuan);
    }
}


.. code-block:: text

    +---+---+
    |   |   |
    |   |   |
    +---+---+


