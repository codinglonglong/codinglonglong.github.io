.. title: Java代码案例3——算术运算
.. slug: javadai-ma-an-li-suan-zhu-yun-suan
.. date: 2022-11-01 22:16:07 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text

.. code-block:: java
    :number-lines:

    // Java算术运算
    package xiangmu;
    import java.util.Scanner;

    public class Ceshi {
        public static void main(String args[]) {
            Scanner sc = new Scanner(System.in);
            System.out.print("请输入第一个正整数：");
            int shuzi1 = sc.nextInt();
            System.out.print("请输入第二个正整数：");
            int shuzi2 = sc.nextInt();
            int jieguo1 = shuzi1 + shuzi2; // 加法 +
            System.out.println(shuzi1 + "+" + shuzi2 + "=" + jieguo1);
            int jieguo2 = shuzi1 - shuzi2; // 减法 -
            System.out.println(shuzi1 + "-" + shuzi2 + "=" + jieguo2);
            int jieguo3 = shuzi1 * shuzi2; // 乘法 *
            System.out.println(shuzi1 + "*" + shuzi2 + "=" + jieguo3);
            float jieguo4 = (float)shuzi1 / shuzi2; // 除法 /
            System.out.println(shuzi1 + "/" + shuzi2 + "=" + jieguo4);
            int jieguo5 = shuzi1 % shuzi2; // 求余数
            System.out.println(shuzi1 + "%" + shuzi2 + "=" + jieguo5);
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

    