.. title: Java代码案例42——嵌套循环输出星号倒三角形
.. slug: javadai-ma-an-li-42-qian-tao-xun-huan-shu-chu-xing-hao-dao-san-jiao-xing
.. date: 2022-12-21 22:14:57 UTC+08:00
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
            // 嵌套循环输出星号三角形
            for(int m = 1; m <= 5; m++) {
                for(int i = 1; i <= m; i++) {
                    System.out.print("*");
                }
                System.out.println();
            }
        }
    }

.. code-block:: text

    *
    **
    ***
    ****
    ***** 

    
