.. title: Java代码案例37——连续输入多个正整数，找到最大值
.. slug: javadai-ma-an-li-37-lian-xu-shu-ru-duo-ge-zheng-zheng-shu-zhao-dao-zui-da-zhi
.. date: 2022-12-15 23:09:50 UTC+08:00
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
            // 连续输入多个正整数，找到最大值
            int shuzi = 0;
            int zuidazhi = -1;
            Scanner sc = new Scanner(System.in);
            while(true) {
                System.out.print("请输入一个正整数(-1结束输入)：");
                shuzi = sc.nextInt();
                if(shuzi == -1) {
                    break;
                }
                if(shuzi > zuidazhi) {
                    zuidazhi = shuzi;
                }
            }
            System.out.println("最大值为：" + zuidazhi);
            sc.close();
        }
    }

.. code-block:: text

    请输入一个正整数(-1结束输入)：10
    请输入一个正整数(-1结束输入)：30
    请输入一个正整数(-1结束输入)：50
    请输入一个正整数(-1结束输入)：30
    请输入一个正整数(-1结束输入)：50
    请输入一个正整数(-1结束输入)：20
    请输入一个正整数(-1结束输入)：-1
    最大值为：50

