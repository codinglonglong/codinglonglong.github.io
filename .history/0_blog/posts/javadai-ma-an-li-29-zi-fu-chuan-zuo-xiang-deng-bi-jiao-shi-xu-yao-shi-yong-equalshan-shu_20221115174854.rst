.. title: Java代码案例29——字符串相等比较时需要使用equals函数
.. slug: javadai-ma-an-li-29-zi-fu-chuan-zuo-xiang-deng-bi-jiao-shi-xu-yao-shi-yong-equalshan-shu
.. date: 2022-11-14 23:38:59 UTC+08:00
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
            String zfc1 = "ab";
            String zfc2 = "ab";
            dayin("zfc1: " + zfc1);
            dayin("zfc2: " + zfc2);
            dayin("1. zfc1 == zfc2       " + (zfc1 == zfc2));
            dayin("2. zfc1.equals(zfc2)  " + (zfc1.equals(zfc2)));
            zfc1 = zfc1 + "c";
            zfc2 = zfc2 + "c";
            dayin("zfc1: " + zfc1);
            dayin("zfc2: " + zfc2);
            dayin("3. zfc1 == zfc2       " + (zfc1 == zfc2));   // 引用类型不能用 == 比较是否相等
            dayin("4. zfc1.equals(zfc2)  " + (zfc1.equals(zfc2)));  // 引用类型使用 equals 函数比较是否相等
        }
        public static void dayin(Object obj) {
            System.out.println(obj);
        }
    }

.. code-block:: text

    zfc1: ab
    zfc2: ab
    1. zfc1 == zfc2       true
    2. zfc1.equals(zfc2)  true
    zfc1: abc
    zfc2: abc
    3. zfc1 == zfc2       false
    4. zfc1.equals(zfc2)  true
