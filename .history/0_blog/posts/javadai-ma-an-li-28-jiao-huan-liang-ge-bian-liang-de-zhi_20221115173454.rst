.. title: Java代码案例28——交换两个变量的值
.. slug: javadai-ma-an-li-28-jiao-huan-liang-ge-bian-liang-de-zhi
.. date: 2022-11-14 23:30:23 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text

.. code-block:: java
    :number-lines:

    package xiangmu;

    public class Ceshi {
        public static void main(String args[]) {
            int a = 3;
            int b = 5;
            int c = 0;  
            dayin("交换前：");
            dayin("a: " + a);
            dayin("b: " + b);
            c = a; // 通过临时变量c存储变量a中的值，避免被直接覆盖
            a = b;
            b = c;
            dayin("交换后：");
            dayin("a: " + a);
            dayin("b: " + b);
        }
        public static void dayin(Object obj) {
            System.out.println(obj);
        }
    }


.. code-block:: text

    交换前：
    a: 3
    b: 5
    交换后：
    a: 5
    b: 3


