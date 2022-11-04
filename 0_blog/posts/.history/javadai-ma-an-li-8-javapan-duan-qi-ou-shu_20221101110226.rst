.. title: Java代码案例8——Java判断奇偶数
.. slug: javadai-ma-an-li-8-javapan-duan-qi-ou-shu
.. date: 2022-11-01 20:58:11 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text

.. code-block:: java
    :number-lines:

    // Java判断奇偶数
    package xiangmu;
    import java.util.Scanner;

    public class Ceshi {
        public static void main(String args[]) {
            Scanner sc = new Scanner(System.in);
            dayin("请输入一个正整数：");
            int shuzi = sc.nextInt();
            if(shuzi % 2 == 0) {
                dayin(shuzi+"是一个偶数");
            }else {
                dayin(shuzi+"是一个奇数");
            }
            sc.close();
        }
        public static void dayin(String zifuchuan) {
            System.out.print(zifuchuan);
        }
    }


.. code-block:: text

请输入一个正整数：11
11是一个奇数

