.. title: Java代码案例29——字符串做相等比较时需要使用equals函数
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
            String a = "ab";
            String b = "ab";
            dayin("1. " + (a == b));
            dayin("2. " + (a.equals(b)));
            a = a + "c";
            b = b + "c";
            dayin("3. " + (a == b));   // 引用类型不能用 == 比较是否相等
            dayin("4. " + (a.equals(b)));  // 引用类型使用 equals 函数比较是否相等
        }
        public static void dayin(Object obj) {
            System.out.println(obj);
        }
    }

.. code-block:: text

    +---+---+
    |   |   |
    |   |   |
    +---+---+


