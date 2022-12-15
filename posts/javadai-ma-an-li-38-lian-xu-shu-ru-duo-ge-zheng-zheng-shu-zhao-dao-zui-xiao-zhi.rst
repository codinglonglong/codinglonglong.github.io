.. title: Java代码案例38——连续输入多个正整数，找到最小值
.. slug: javadai-ma-an-li-38-lian-xu-shu-ru-duo-ge-zheng-zheng-shu-zhao-dao-zui-xiao-zhi
.. date: 2022-12-15 23:17:23 UTC+08:00
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
            // 连续输入多个正整数，找到最小值
            int shuzi = 0;
            Scanner sc = new Scanner(System.in);
            System.out.print("请输入一个正整数(-1结束输入)：");
            int zuixiaozhi = sc.nextInt();
            while(zuixiaozhi != -1) {
                System.out.print("请输入一个正整数(-1结束输入)：");
                shuzi = sc.nextInt();
                if(shuzi == -1) {
                    break;
                }
                if(shuzi < zuixiaozhi) {
                    zuixiaozhi = shuzi;
                }
            }
            System.out.println("最小值为：" + zuixiaozhi);
            sc.close();
        }
    }


.. code-block:: text

    请输入一个正整数(-1结束输入)：10
    请输入一个正整数(-1结束输入)：20
    请输入一个正整数(-1结束输入)：30
    请输入一个正整数(-1结束输入)：6
    请输入一个正整数(-1结束输入)：3
    请输入一个正整数(-1结束输入)：6
    请输入一个正整数(-1结束输入)：3
    请输入一个正整数(-1结束输入)：10
    请输入一个正整数(-1结束输入)：-1
    最小值为：3

    