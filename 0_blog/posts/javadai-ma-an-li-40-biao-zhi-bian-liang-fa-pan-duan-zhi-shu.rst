.. title: Java代码案例40——标志变量法判断质数
.. slug: javadai-ma-an-li-40-biao-zhi-bian-liang-fa-pan-duan-zhi-shu
.. date: 2022-12-15 23:51:48 UTC+08:00
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
            // 标志变量法判断质数
            // 质数：只能被 1 和 自己 整除的正整数
            int shuzi = 97;
            int biaozhi = 0;
            for(int i=2; i<shuzi; i++) {
                if(shuzi % i == 0) {
                    biaozhi = 1;
                    break;
                }
            }
            if(biaozhi == 0) {
                System.out.println(shuzi + "是一个质数！");
            }else {
                System.out.println(shuzi + "不是质数！");
            }
        }
    }


.. code-block:: text

    97是一个质数！

