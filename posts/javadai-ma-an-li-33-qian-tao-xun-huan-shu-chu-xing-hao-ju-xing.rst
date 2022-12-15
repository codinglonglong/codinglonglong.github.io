.. title: Java代码案例33——嵌套循环输出星号矩形
.. slug: javadai-ma-an-li-33-qian-tao-xun-huan-shu-chu-xing-hao-ju-xing
.. date: 2022-12-15 22:30:05 UTC+08:00
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
            // 打印 5 行 8 列 星号矩形
            // 嵌套循环
            for(int i=0; i<5; i++) {
                for(int j=0; j<8; j++) {
                    System.out.print("*");
                }
                System.out.println();
            }
        }
    }

.. code-block:: text

    ********
    ********
    ********
    ********
    ********

