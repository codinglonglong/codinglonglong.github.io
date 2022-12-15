.. title: Java代码案例36——用户输入一个英文字符串，统计英文、数字、符号和空格的个数
.. slug: javadai-ma-an-li-36-yong-hu-shu-ru-yi-ge-ying-wen-zi-fu-chuan-tong-ji-ying-wen-shu-zi-fu-hao-he-kong-ge-de-ge-shu
.. date: 2022-12-15 22:56:51 UTC+08:00
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
            // 用户输入一个英文字符串，统计英文、数字、符号和空格的个数
            System.out.print("请输入一个包含英文、数字、符号和空格的字符串：");
            Scanner sc = new Scanner(System.in);
            String zfc = sc.nextLine();     // 读取一行字符，可以包含空格
            sc.close();
            int jishu_yingwen = 0;
            int jishu_shuzi = 0;
            int jishu_fuhao = 0;
            int jishu_kongge = 0;
            for (int i = 0; i < zfc.length(); i++) {
                if ((zfc.charAt(i) >= 'A' && zfc.charAt(i) <= 'Z') || (zfc.charAt(i) >= 'a' && zfc.charAt(i) <= 'z')) {
                    jishu_yingwen = jishu_yingwen + 1;
                } else if (zfc.charAt(i) >= '0' && zfc.charAt(i) <= '9') {
                    jishu_shuzi = jishu_shuzi + 1;
                } else if (zfc.charAt(i) != ' ') {
                    jishu_fuhao = jishu_fuhao + 1;
                } else {
                    jishu_kongge = jishu_kongge + 1;
                }
            }
            System.out.println("英文共有" + jishu_yingwen + "个");
            System.out.println("数字共有" + jishu_shuzi + "个");
            System.out.println("符号共有" + jishu_fuhao + "个");
            System.out.println("空格共有" + jishu_kongge + "个");
        }
    }



.. code-block:: text

    请输入一个包含英文、数字、符号和空格的字符串：I'm 20 years old.
    英文共有10个
    数字共有2个
    符号共有2个
    空格共有3个

