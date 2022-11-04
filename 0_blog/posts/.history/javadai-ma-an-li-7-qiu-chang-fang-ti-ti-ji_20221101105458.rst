.. title: Java代码案例7——求长方体体积
.. slug: javadai-ma-an-li-7-qiu-chang-fang-ti-ti-ji
.. date: 2022-11-01 20:54:05 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text


.. code-block:: java
    :number-lines:

    // Java求长方体体积
    package xiangmu;
    import java.util.Scanner;

    public class Ceshi {
        public static void main(String args[]) {
            Scanner sc = new Scanner(System.in);
            dayin("请输入长方体的长：");
            int ch = sc.nextInt();
            dayin("请输入长方体的宽：");
            int k = sc.nextInt();
            dayin("请输入长方体的高：");
            int g = sc.nextInt();
            int tiji = qiutiji(ch, k, g);
            dayin("这个长方体的体积为：" + tiji);
            sc.close();
        }
        public static int qiutiji(int chang, int kuan, int gao) {
            int t = chang * kuan * gao;
            return t;
        }
        public static void dayin(String zifuchuan) {
            System.out.print(zifuchuan);
        }
    }



.. code-block:: text

    请输入长方体的长：5
    请输入长方体的宽：3
    请输入长方体的高：4
    这个长方体的体积为：60


