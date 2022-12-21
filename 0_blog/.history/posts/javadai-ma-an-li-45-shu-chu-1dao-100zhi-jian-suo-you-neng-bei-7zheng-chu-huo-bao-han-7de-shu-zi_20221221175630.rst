.. title: Java代码案例45——输出1到100之间所有能被7整除或包含7的数字
.. slug: javadai-ma-an-li-45-shu-chu-1dao-100zhi-jian-suo-you-neng-bei-7zheng-chu-huo-bao-han-7de-shu-zi
.. date: 2022-12-21 22:55:46 UTC+08:00
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
            // 输出1到100之间所有能被7整除或包含7的数字
            // 方法1
            // String.valueOf(i) 数字转成字符串
            // zfc.contains("7") 判断字符串zfc中是否包含子串7
            for(int i = 1; i <= 100; i = i + 1) {
                if(i % 7 == 0 || String.valueOf(i).contains("7")){
                    System.out.print(i + " ");
                }
            }
            System.out.println();
            // 方法2
            // zfc.indexOf("7") 返回字符串zfc中子串7所在的下标，如果找不到，返回-1
            for(int i = 1; i <= 100; i = i + 1) {
                if(i % 7 == 0 || String.valueOf(i).indexOf("7") > -1){
                    System.out.print(i + " ");
                }
            }
        }
    }

.. code-block:: text

    
