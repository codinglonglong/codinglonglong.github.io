.. title: Java代码案例15——三个正整数求最大值1
.. slug: javadai-ma-an-li-15-san-ge-zheng-zheng-shu-qiu-zui-da-zhi-1
.. date: 2022-11-01 21:50:59 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text

.. code-block:: java
    :number-lines:

    // Java三个正整数求最大值——多分支
    package xiangmu;

    public class Ceshi {
        public static void main(String args[]) {
            int a = 3;
            int b = 5;
            int c = 4;
            if(a >= b && a >= c) {
                dayin("最大值是：" + a);
            }else if(b >= c) {
                dayin("最大值是：" + b);
            }else {
                dayin("最大值是：" + c);
            }
        }
        public static void dayin(String zifuchuan) {
            System.out.println(zifuchuan);
        }
    }



.. code-block:: text

    最大值是：5

