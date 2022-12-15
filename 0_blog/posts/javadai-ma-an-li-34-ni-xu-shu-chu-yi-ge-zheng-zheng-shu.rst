.. title: Java代码案例34——逆序输出一个正整数
.. slug: javadai-ma-an-li-34-ni-xu-shu-chu-yi-ge-zheng-zheng-shu
.. date: 2022-12-15 22:38:47 UTC+08:00
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
            // 逆序输出一个正整数
            int shuzi = 12345;
            while(shuzi!=0) {
                int yushu = shuzi % 10;
                System.out.print(yushu);
                shuzi = shuzi / 10;
            }
        }
    }

.. code-block:: text

    54321

