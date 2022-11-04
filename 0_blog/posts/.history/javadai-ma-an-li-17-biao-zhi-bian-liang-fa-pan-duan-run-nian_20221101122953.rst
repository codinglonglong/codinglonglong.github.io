.. title: Java代码案例17——标志变量法判断闰年
.. slug: javadai-ma-an-li-17-biao-zhi-bian-liang-fa-pan-duan-run-nian
.. date: 2022-11-02 00:00:42 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text

.. code-block:: java
    :number-lines:

    // Java判断闰年——嵌套分支，标志变量
    // 闰年：能被4整除并且不能被100整除，或者能被400整除
    package xiangmu;

    public class Ceshi {
        public static void main(String args[]) {
            int nian = 1900;
            int biaozhi = 0;
            if(nian % 4 == 0) {
                if(nian % 100 != 0) {
                    biaozhi = 1;
                }
            }
            if(nian % 400 == 0) {
                biaozhi = 1;
            }
            if(biaozhi == 1) {
                dayin(nian + "是闰年");
            }else {
                dayin(nian + "不是闰年");
            }
        }
        public static void dayin(String zifuchuan) {
            System.out.println(zifuchuan);
        }
    }

.. code-block:: text

    1900不是闰年


