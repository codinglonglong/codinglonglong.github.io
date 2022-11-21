.. title: Java“并且&&”运算真值表测试
.. slug: javabing-qie-yun-suan-zhen-zhi-biao-ce-shi
.. date: 2022-11-20 21:55:04 UTC+08:00
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
            // 真值表“&&并且”测试
            int chengji = 85;
            if(chengji >= 60 && chengji <= 90) {
                System.out.println("1. 条件A为真，条件B为真，条件A && 条件B 的结果为真。");
            }else {
                System.out.println("1. 条件A为真，条件B为真，条件A && 条件B 的结果为假。");
            }
            if(chengji >= 60 && chengji >= 90) {
                System.out.println("2. 条件A为真，条件B为假，条件A && 条件B 的结果为真。");
            }else {
                System.out.println("2. 条件A为真，条件B为假，条件A && 条件B 的结果为假。");
            }
            if(chengji <= 60 && chengji <= 90) {
                System.out.println("3. 条件A为假，条件B为真，条件A && 条件B 的结果为真。");
            }else {
                System.out.println("3. 条件A为假，条件B为真，条件A && 条件B 的结果为假。");
            }
            if(chengji <= 60 && chengji >= 90) {
                System.out.println("4. 条件A为假，条件B为假，条件A && 条件B 的结果为真。");
            }else {
                System.out.println("4. 条件A为假，条件B为假，条件A && 条件B 的结果为假。");
            }
        }	
    }

.. code-block:: text

    1. 条件A为真，条件B为真，条件A && 条件B 的结果为真。
    2. 条件A为真，条件B为假，条件A && 条件B 的结果为假。
    3. 条件A为假，条件B为真，条件A && 条件B 的结果为假。
    4. 条件A为假，条件B为假，条件A && 条件B 的结果为假。

    