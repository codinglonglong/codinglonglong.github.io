.. title: Java代码案例10——多分支判断星期
.. slug: javadai-ma-an-li-10-duo-fen-zhi-pan-duan-xing-qi
.. date: 2022-11-01 21:14:28 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text

.. code-block:: java
    :number-lines:

    // Java多分支判断星期
    package xiangmu;

    public class Ceshi {
        public static void main(String args[]) {
            int xingqi = 3;
            if(xingqi == 1) {
                dayin("星期一");
            }else if(xingqi == 2) {
                dayin("星期二");
            }else if(xingqi == 3) {
                dayin("星期三");
            }else if(xingqi == 4) {
                dayin("星期四");
            }else if(xingqi == 5) {
                dayin("星期五");
            }else {
                dayin("周末");
            }
        }
        public static void dayin(String zifuchuan) {
            System.out.println(zifuchuan);
        }
    }


.. code-block:: text

    星期三

