.. title: Java基本数据类型存储范围
.. slug: javaji-ben-shu-ju-lei-xing-cun-chu-fan-wei
.. date: 2022-11-23 22:06:51 UTC+08:00
.. tags: Java
.. category: Java
.. link: 
.. description: 
.. type: text


.. code-block:: java
    :number-lines:

    package xiangmu;

    public class Ceshi {
        public static void main(String args[]) {
            System.out.println("byte类型可以存储的最大值: "+Byte.MAX_VALUE);
            System.out.println("byte类型可以存储的最小值: "+Byte.MIN_VALUE);
            System.out.println("short类型可以存储的最大值: "+Short.MAX_VALUE);
            System.out.println("short类型可以存储的最小值: "+Short.MIN_VALUE);
            System.out.println("int类型可以存储的最大值: "+Integer.MAX_VALUE);
            System.out.println("int类型可以存储的最小值: "+Integer.MIN_VALUE);
            System.out.println("long类型可以存储的最大值: "+Long.MAX_VALUE);
            System.out.println("long类型可以存储的最小值: "+Long.MIN_VALUE);
            System.out.println("float类型可以存储的最大值: "+Float.MAX_VALUE);
            System.out.println("float类型可以存储的最小值: "+Float.MIN_VALUE);
            System.out.println("double类型可以存储的最大值: "+Double.MAX_VALUE);
            System.out.println("double类型可以存储的最小值: "+Double.MIN_VALUE);
        }	
    }


.. code-block:: text

byte类型可以存储的最大值: 127
byte类型可以存储的最小值: -128
short类型可以存储的最大值: 32767
short类型可以存储的最小值: -32768
int类型可以存储的最大值: 2147483647
int类型可以存储的最小值: -2147483648
long类型可以存储的最大值: 9223372036854775807
long类型可以存储的最小值: -9223372036854775808
float类型可以存储的最大值: 3.4028235E38
float类型可以存储的最小值: 1.4E-45
double类型可以存储的最大值: 1.7976931348623157E308
double类型可以存储的最小值: 4.9E-324
