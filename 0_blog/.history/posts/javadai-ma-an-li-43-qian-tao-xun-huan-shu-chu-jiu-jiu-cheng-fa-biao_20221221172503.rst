.. title: Java代码案例43——嵌套循环输出九九乘法表
.. slug: javadai-ma-an-li-43-qian-tao-xun-huan-shu-chu-jiu-jiu-cheng-fa-biao
.. date: 2022-12-21 22:24:19 UTC+08:00
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
            // 嵌套循环输出九九乘法表
            // \t 水平制表符   \n 换行符
            for(int m = 1; m <= 9; m++) {
                for(int n = 1; n <= m; n++) {
                    System.out.print(n+"*"+m+"="+m*n+"\t");
                }
                System.out.print("\n"); 
            }
        }
    }

.. code-block:: text
