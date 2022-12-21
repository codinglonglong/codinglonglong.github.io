.. title: Java代码案例44——三种循环计算从1连加到100的正整数和
.. slug: javadai-ma-an-li-44-san-chong-xun-huan-ji-suan-cong-1lian-jia-dao-100de-zheng-zheng-shu-he
.. date: 2022-12-21 22:41:28 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text


.. code-block:: java
    :number-lines:

    package xiangmu;

    public class Ceshi {
        public static void main(String args[]) {
            // 三种循环计算从1连加到100的正整数和
            // while 循环
            int i = 1;
            int he = 0;
            while(i <= 100) {
                he = he + i;
                i = i + 1;
            }
            System.out.println("1 + 2 + 3 + ... + 99 + 100 = " + he);
            // do...while 循环
            int j = 1;
            int he1 = 0;
            do {
                he1 = he1 + j;
                j = j + 1;
            }while(j <= 100);
            System.out.println("1 + 2 + 3 + ... + 99 + 100 = " + he1);
            // for 循环
            int he2 = 0;
            for(int k = 1; k <= 100; k=k+1) {
                he2 = he2 + k;
            }
            System.out.println("1 + 2 + 3 + ... + 99 + 100 = " + he2);
        }
    }


.. code-block:: text

1 + 2 + 3 + ... + 99 + 100 = 5050
1 + 2 + 3 + ... + 99 + 100 = 5050
1 + 2 + 3 + ... + 99 + 100 = 5050
