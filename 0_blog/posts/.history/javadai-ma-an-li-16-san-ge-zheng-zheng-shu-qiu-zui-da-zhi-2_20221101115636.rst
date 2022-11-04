.. title: Java代码案例16——三个正整数求最大值2
.. slug: javadai-ma-an-li-16-san-ge-zheng-zheng-shu-qiu-zui-da-zhi-2
.. date: 2022-11-01 11:56:08 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text

.. code-block:: java
    :number-lines:

    // Java三个正整数求最大值——嵌套分支
    package xiangmu;

    public class Ceshi {
        public static void main(String args[]) {
            int a = 9;
            int b = 10;
            int c = 8;
            if(a >= b) {
                if(a >= c) {
                    dayin("最大值是：" + a);
                }else {
                    dayin("最大值是：" + c);
                }
            }else {
                if(b >= c) {
                    dayin("最大值是：" + b);
                }else {
                    dayin("最大值是：" + c);
                }
            }
        }
        public static void dayin(String zifuchuan) {
            System.out.println(zifuchuan);
        }
    }


.. code-block:: text

    你好

