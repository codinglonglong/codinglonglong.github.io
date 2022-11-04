.. title: Java代码案例——算术运算
.. slug: javadai-ma-an-li-suan-zhu-yun-suan
.. date: 2022-11-01 10:16:07 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text

.. code-block:: java
    :number-lines:

    // Java输入、存储、输出
    package xiangmu;
    import java.util.Scanner;

    public class Ceshi {
        public static void main(String args[]) {
            System.out.print("请输入用户名：");
            Scanner sc = new Scanner(System.in);
            String yonghuming = sc.next();    // 变量
            System.out.print("你好，"+yonghuming);
            sc.close();
        }
    }


.. code-block:: bash

    请输入用户名：张三
    你好，张三

    