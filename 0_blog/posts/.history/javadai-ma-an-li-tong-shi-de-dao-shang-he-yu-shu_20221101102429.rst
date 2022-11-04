.. title: Java代码案例——同时得到商和余数
.. slug: javadai-ma-an-li-tong-shi-de-dao-shang-he-yu-shu
.. date: 2022-11-01 10:23:45 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text


.. code-block:: java
    :number-lines:

    // Java同时得到商和余数
    package xiangmu;
    import java.util.Scanner;

    public class Ceshi {
        public static void main(String args[]) {
            Scanner sc = new Scanner(System.in);
            System.out.print("请输入第一个正整数：");
            int shuzi1 = sc.nextInt();
            System.out.print("请输入第二个正整数：");
            int shuzi2 = sc.nextInt();
            int shang = shuzi1 / shuzi2;
            int yushu = shuzi1 % shuzi2;
            System.out.println(shuzi1 + "/" + shuzi2 + "=" + shang + "..." + yushu);
            sc.close();
        }
    }



.. code-block:: text

    请输入第一个正整数：13
    请输入第二个正整数：5
    13+5=18
    13-5=8
    13*5=65
    13/5=2.6
    13%5=3

    
