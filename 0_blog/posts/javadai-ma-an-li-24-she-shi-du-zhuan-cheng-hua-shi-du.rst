.. title: Java代码案例24——摄氏度转成华氏度
.. slug: javadai-ma-an-li-24-she-shi-du-zhuan-cheng-hua-shi-du
.. date: 2022-11-14 22:15:40 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text


.. code-block:: java
    :number-lines:

    package xiangmu;
    import java.util.Scanner;

    public class Ceshi {
        public static void main(String args[]) {
            Scanner sc = new Scanner(System.in);
            System.out.print("请输入摄氏度:");
            float sheshi = sc.nextFloat();
            // 注意这里的 (float) 必须要写，否则9/5先按整数算，会丢掉小数，导致计算错误
            float huashi = ((float)9/5) * sheshi + 32;   
            System.out.print(sheshi+"摄氏度等于"+huashi+"华氏度。");
        }
    }



.. code-block:: text

    请输入摄氏度:37.3
    37.3摄氏度等于99.14华氏度。

