.. title: Java代码案例6——求长方形面积
.. slug: javadai-ma-an-li-qiu-chang-fang-xing-mian-ji
.. date: 2022-11-01 20:39:57 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text

.. code-block:: java
    :number-lines:

    // Java求长方形面积
    package xiangmu;
    import java.util.Scanner;

    public class Ceshi {
        public static void main(String args[]) {
            Scanner sc = new Scanner(System.in);
            dayin("请输入长方形的长：");
            int ch = sc.nextInt();
            dayin("请输入长方形的宽：");
            int k = sc.nextInt();
            int mianji = qiumianji(ch, k);
            dayin("这个长方形的面积为：" + mianji);
            sc.close();
        }
        public static int qiumianji(int chang, int kuan) {
            int m = chang * kuan;
            return m;
        }
        public static void dayin(String zifuchuan) {
            System.out.print(zifuchuan);
        }
    }


.. code-block:: text

    请输入长方形的长：5
    请输入长方形的宽：3
    这个长方形的面积为：15

