.. title: Java代码案例14——逻辑运算符判断闰年2
.. slug: javadai-ma-an-li-14-luo-ji-yun-suan-fu-pan-duan-run-nian-2
.. date: 2022-11-01 21:36:28 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text

.. code-block:: java
    :number-lines:

    // Java逻辑运算符判断闰年
    // 闰年：能被4整除并且不能被100整除，或者能被400整除
    // 注意：并且&&的优先级高于或者||
    package xiangmu;

    public class Ceshi {
        public static void main(String args[]) {
            int nian = 2000;
            if(nian % 400 == 0 || nian % 4 == 0 && nian % 100 != 0 ) {
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

    2000是闰年

