.. title: Java代码案例13——逻辑运算符判断闰年1
.. slug: javadai-ma-an-li-13-luo-ji-yun-suan-fu-pan-duan-run-nian-1
.. date: 2022-11-01 11:30:00 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text


.. code-block:: java
    :number-lines:

    // Java逻辑运算符判断闰年
    package xiangmu;

    public class Ceshi {
        public static void main(String args[]) {
            int nian = 1900;
            if(nian % 4 == 0 && nian % 100 != 0 || nian % 400 == 0) {
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


