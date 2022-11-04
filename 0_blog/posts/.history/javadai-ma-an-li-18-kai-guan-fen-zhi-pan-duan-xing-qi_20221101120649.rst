.. title: Java代码案例18——开关分支判断星期
.. slug: javadai-ma-an-li-18-kai-guan-fen-zhi-pan-duan-xing-qi
.. date: 2022-11-01 22:06:00 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text

.. code-block:: java
    :number-lines:

    // Java开关分支判断星期
    package xiangmu;

    public class Ceshi {
        public static void main(String args[]) {
            int xingqi = 3;
            switch(xingqi) {
                case 1: 
                    dayin("星期一");
                    break;
                case 2: 
                    dayin("星期二");
                    break;
                case 3: 
                    dayin("星期三");
                    break;
                case 4: 
                    dayin("星期四");
                    break;
                case 5: 
                    dayin("星期五");
                    break;
                default: 
                    dayin("周末");
            }
        }
        public static void dayin(String zifuchuan) {
            System.out.println(zifuchuan);
        }
    }




.. code-block:: text

    星期三

    

