.. title: Java代码案例35——字符串方式逆序输出一个正整数
.. slug: javadai-ma-an-li-35-zi-fu-chuan-fang-shi-ni-xu-shu-chu-yi-ge-zheng-zheng-shu
.. date: 2022-12-15 22:48:33 UTC+08:00
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
            // 字符串方式逆序输出一个正整数
            int shuzi = 123456;
            String sz = String.valueOf(shuzi);
            for(int i = sz.length()-1; i>=0; i--) {
                System.out.print(sz.charAt(i));
            }
        }
    }


.. code-block:: text

    654321

    