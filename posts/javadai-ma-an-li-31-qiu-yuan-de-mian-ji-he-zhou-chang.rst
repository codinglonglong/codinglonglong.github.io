.. title: Java代码案例31——求圆的面积和周长
.. slug: javadai-ma-an-li-31-qiu-yuan-de-mian-ji-he-zhou-chang
.. date: 2022-12-15 21:52:13 UTC+08:00
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
            // 计算圆的面积和周长
            double r = 3;
            final double PI = 3.14159;   // 命名常量，一次赋值，不可更改
            double mianji = PI * r * r;
            System.out.println("面积为：" + String.format("%.3f", mianji)); // 保留三位小数
            double zhouchang = 2 * PI * r;
            System.out.println("周长为：" + String.format("%.3f", zhouchang));
        }
    }

.. code-block:: text

    面积为：28.274
    周长为：18.850

