.. title: Java代码案例47——利用字符编码进行字符串加密和解密
.. slug: javadai-ma-an-li-47-li-yong-zi-fu-bian-ma-jin-xing-zi-fu-chuan-jia-mi-he-jie-mi
.. date: 2022-12-21 23:21:38 UTC+08:00
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
            // 利用ASCII码表对字符串进行加密和解密
            String zifuchuan = "I'm 20 years old.";
            // 密钥是正整数，假定为3，这个是加密和解密的钥匙
            // 修改密钥可以得到不同的加密后的字符串
            int miyao = 3;  
            System.out.println("原始字符串为：" + zifuchuan);
            String jiamihou = jiami(zifuchuan, miyao);
            System.out.println("加密后的字符串为：" + jiamihou);
            String jiemihou = jiemi(jiamihou, miyao);
            System.out.println("解密后的字符串为：" + jiemihou);
        }
        public static String jiami(String zfc, int my) {
            // zfc 要加密的字符串
            // my 约定好的密钥
            String xinzfc = "";
            for(int i = 0; i < zfc.length(); i = i + 1) {
                xinzfc = xinzfc + (char)(zfc.charAt(i) + my);
            }
            return xinzfc;
        }
        public static String jiemi(String zfc, int my) {
            // zfc 要解密的字符串
            // my 约定好的密钥
            String xinzfc = "";
            for(int i = 0; i < zfc.length(); i = i + 1) {
                xinzfc = xinzfc + (char)(zfc.charAt(i) - my);
            }
            return xinzfc;
        }
    }

.. code-block:: text

    原始字符串为：I'm 20 years old.
    加密后的字符串为：L*p#53#|hduv#rog1
    解密后的字符串为：I'm 20 years old.
