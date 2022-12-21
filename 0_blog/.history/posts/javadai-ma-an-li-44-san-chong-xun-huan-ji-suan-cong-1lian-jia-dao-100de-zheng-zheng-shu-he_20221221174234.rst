.. title: Java代码案例44——三种循环计算从1连加到100的正整数和
.. slug: javadai-ma-an-li-44-san-chong-xun-huan-ji-suan-cong-1lian-jia-dao-100de-zheng-zheng-shu-he
.. date: 2022-12-21 22:41:28 UTC+08:00
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
            // 嵌套循环输出星号倒三角形
            for(int m = 1; m <= 5; m++) {
                for(int i = 1; i <= (5-m)+1; i++) {
                    System.out.print("*");
                }
                System.out.println();
            }
        }
    }

.. code-block:: text

    *****
    ****
    ***
    **
    *


