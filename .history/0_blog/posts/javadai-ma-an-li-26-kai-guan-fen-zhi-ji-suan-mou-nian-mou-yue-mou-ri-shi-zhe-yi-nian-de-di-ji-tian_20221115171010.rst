.. title: Java代码案例26——开关分支计算某年某月某日是这一年的第几天
.. slug: javadai-ma-an-li-26-kai-guan-fen-zhi-ji-suan-mou-nian-mou-yue-mou-ri-shi-zhe-yi-nian-de-di-ji-tian
.. date: 2022-11-14 23:09:03 UTC+08:00
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
            int nian = 2020;
            int yue = 3;
            int ri = 5;
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
                case 3: 
                    if(nian % 4 == 0 && nian % 100 != 0 || nian % 400 == 0) {
                        tian = tian + 29;
                    }else {
                        tian = tian + 28;
                    }
                case 2: tian = tian + 31;
                case 1: tian = tian + ri;
            }
            dayin(nian + "年"+yue+"月"+ri+"日是这一年的第"+tian+"天");
        }
        public static void dayin(String zifuchuan) {
            System.out.println(zifuchuan);
        }
    }

.. code-block:: text

    2022年3月5日是这一年的第64天

