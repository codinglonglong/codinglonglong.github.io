.. title: Java代码案例9——比较运算
.. slug: javadai-ma-an-li-9-bi-jiao-yun-suan
.. date: 2022-11-01 21:05:58 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text


.. code-block:: java
    :number-lines:

    // Java比较运算
    package xiangmu;

    public class Ceshi {
        public static void main(String args[]) {
            int a = 5;
            if(a == 5) {
                dayin(a + "等于5");
            }
            if(a != 3) {
                dayin(a + "不等于3");
            }
            if(a > 1) {
                dayin(a + "大于1");
            }
            if(a >= 5) {
                dayin(a + "大于等于5");
            }
            if(a < 6) {
                dayin(a + "小于6");
            }
            if(a <= 5) {
                dayin(a + "小于等于5");
            }
        }
        public static void dayin(String zifuchuan) {
            System.out.println(zifuchuan);
        }
    }


.. code-block:: text

    5等于5
    5不等于3
    5大于1
    5大于等于5
    5小于6
    5小于等于5

