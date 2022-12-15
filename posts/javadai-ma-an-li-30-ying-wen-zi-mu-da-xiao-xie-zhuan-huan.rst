.. title: Java代码案例30——英文字母大小写转换
.. slug: javadai-ma-an-li-30-ying-wen-zi-mu-da-xiao-xie-zhuan-huan
.. date: 2022-12-15 21:31:22 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text


.. code-block:: java
    :number-lines:

    package xiangmu;

    import java.util.Scanner;

    public class Ceshi {
        public static void main(String args[]) {
            /* 用户输入一个字母，
            * 如果是大写字母，程序自动转化成小写字母并输出；
            * 如果是小写字母，程序自动转化成大写字母并输出
            */
            System.out.print("请输入一个字母：");
            Scanner sc = new Scanner(System.in);
            char zifu = sc.next().charAt(0);   // 获取用户输入的单个字符
            if (zifu >= 'A' && zifu <= 'Z') {
                zifu = (char)(zifu + 32);
                System.out.println("转化成小写字母为：" + zifu);
            }else if(zifu >= 'a' && zifu <= 'z') {
                zifu = (char)(zifu - 32);
                System.out.println("转化成大写字母为：" + zifu);
            }else {
                System.out.println("非法字符！");
            }
            sc.close();
        }
    }


.. code-block:: text

    请输入一个字母：h
    转化成大写字母为：H

