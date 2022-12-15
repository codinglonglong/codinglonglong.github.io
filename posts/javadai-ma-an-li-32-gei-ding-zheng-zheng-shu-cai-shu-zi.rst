.. title: Java代码案例32——给定正整数，猜数字
.. slug: javadai-ma-an-li-32-gei-ding-zheng-zheng-shu-cai-shu-zi
.. date: 2022-12-15 22:16:12 UTC+08:00
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
            // 给定正整数，猜数字游戏
            int shuzi = 51;
            System.out.println("欢迎来到猜数字游戏！");
            System.out.print("请输入一个0到100之间的整数：");
            Scanner sc = new Scanner(System.in);
            while(true) {
                int sz = sc.nextInt();
                if(sz < 0 || sz > 100) {
                    System.out.print("输入非法！请继续猜数字：");
                    continue;                           // continue 跳过本次循环  
                }
                if(sz > shuzi) {
                    System.out.print("猜高了！");
                }else if(sz < shuzi) {
                    System.out.print("猜低了！");
                }else {
                    System.out.println("猜对了！");
                    System.out.println("程序退出...");
                    break;                              // break 跳出本层循环    
                }
                System.out.print("请继续猜数字：");
            }
            sc.close();
        }
    }

.. code-block:: text

    欢迎来到猜数字游戏！
    请输入一个0到100之间的整数：1000
    输入非法！请继续猜数字：-1
    输入非法！请继续猜数字：50
    猜低了！请继续猜数字：53
    猜高了！请继续猜数字：51
    猜对了！
    程序退出...

