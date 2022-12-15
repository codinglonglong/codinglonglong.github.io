.. title: Java代码案例39——随机生成0到100之间的正整数，猜数字游戏
.. slug: javadai-ma-an-li-39-sui-ji-sheng-cheng-0dao-100zhi-jian-de-zheng-zheng-shu-cai-shu-zi-you-xi
.. date: 2022-12-15 23:35:05 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text


.. code-block:: java
    :number-lines:

    package xiangmu;

    import java.util.Random;
    import java.util.Scanner;

    public class Ceshi {
        public static void main(String args[]) {
            // 随机生成0到100之间的正整数，猜数字游戏
            Random r = new Random();
            int shuzi = r.nextInt(101);  // nextInt(m) 生成 [0, m-1] 范围的正整数
            System.out.println("欢迎来到猜数字游戏！目标数字已生成！");
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
                    System.out.println("猜对了！目标数字是：" + shuzi);
                    System.out.println("程序退出...");
                    break;                              // break 跳出本层循环
                }
                System.out.print("请继续猜数字：");
            }
            sc.close();
        }
    }


.. code-block:: text

    欢迎来到猜数字游戏！目标数字已生成！
    请输入一个0到100之间的整数：50
    猜高了！请继续猜数字：-5
    输入非法！请继续猜数字：1000
    输入非法！请继续猜数字：25
    猜高了！请继续猜数字：12
    猜高了！请继续猜数字：6
    猜高了！请继续猜数字：3
    猜低了！请继续猜数字：4
    猜低了！请继续猜数字：5
    猜对了！目标数字是：5
    程序退出...

