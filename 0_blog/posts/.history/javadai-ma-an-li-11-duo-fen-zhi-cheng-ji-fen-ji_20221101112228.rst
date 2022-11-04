.. title: Java代码案例11——多分支成绩分级
.. slug: javadai-ma-an-li-11-duo-fen-zhi-cheng-ji-fen-ji
.. date: 2022-11-01 21:21:08 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text


.. code-block:: java
    :number-lines:

    // Java多分支成绩分级，注意判断条件的顺序
    package xiangmu;

    public class Ceshi {
        public static void main(String args[]) {
            int chengji = 85;
            if(chengji == 100) {
                dayin("满分");
            }else if(chengji >= 80) {
                dayin("优秀");
            }else if(chengji >= 60) {
                dayin("及格");
            }else {
                dayin("不及格");
            }
        }
        public static void dayin(String zifuchuan) {
            System.out.println(zifuchuan);
        }
    }




.. code-block:: text

    你好

