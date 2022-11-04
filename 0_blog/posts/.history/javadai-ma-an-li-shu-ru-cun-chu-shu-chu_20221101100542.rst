.. title: Java代码案例——输入、存储、输出
.. slug: javadai-ma-an-li-shu-ru-cun-chu-shu-chu
.. date: 2022-11-01 10:04:22 UTC+08:00
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


