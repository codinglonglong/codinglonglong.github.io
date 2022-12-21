.. title: Java代码案例48——求解鸡兔同笼问题
.. slug: javadai-ma-an-li-48-qiu-jie-ji-tu-tong-long-wen-ti
.. date: 2022-12-21 23:34:51 UTC+08:00
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
            // 求解鸡兔同笼问题
            // 给定头的总数和脚的总数，求解共有多少只鸡和多少只兔子
            int tou = 35;   // 头的总数
            int jiao = 94;  // 脚的总数
            int ji = 0;     // 鸡的总数
            int tu = 0;		// 兔的总数
            int biaozhi = 0;  // 标志变量，标记是否找到问题的解
            for(ji = 0; ji <= tou; ji = ji + 1) {
                if(ji * 2 + (tou - ji) * 4 == jiao) {
                    tu = tou - ji;
                    biaozhi = 1;
                    break;
                }
            }
            if(biaozhi == 1) {
                System.out.println("共有"+ ji + "只鸡，" + tu + "只兔子。");
            }else {
                System.out.println("此题无解！");
            }
        }
    }


