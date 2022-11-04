.. title: Java代码案例20——Java开关分支计算某月某日是2022年的第几天
.. slug: javadai-ma-an-li-20-javakai-guan-fen-zhi-ji-suan-mou-yue-mou-ri-shi-2022nian-de-di-ji-tian
.. date: 2022-11-01 22:23:41 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text

.. code-block:: java
    :number-lines:

    // Java开关分支计算某月某日是2022年的第几天
    // 固定年份，暂不考虑闰年的问题
    package xiangmu;

    public class Ceshi {
        public static void main(String args[]) {
            int yue = 10;
            int ri = 21;
            int tian = 0;
            switch(yue) {
                case 12: tian = tian + 30;
                case 11: tian = tian + 31;
                case 10: tian = tian + 30;
                case 9: tian = tian + 31;
                case 8: tian = tian + 31;
                case 7: tian = tian + 30;
                case 6: tian = tian + 31;
                case 5: tian = tian + 30;
                case 4: tian = tian + 31;
                case 3:	tian = tian + 28;
                case 2:	tian = tian + 31;
                case 1: tian = tian + ri;
            }
            dayin("2022年"+yue+"月"+ri+"日是这一年的第"+tian+"天");
        }
        public static void dayin(String zifuchuan) {
            System.out.println(zifuchuan);
        }
    }


.. code-block:: text

    你好

