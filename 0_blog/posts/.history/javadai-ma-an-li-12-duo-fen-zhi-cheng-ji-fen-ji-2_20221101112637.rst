.. title: Java代码案例12——多分支成绩分级2
.. slug: javadai-ma-an-li-11-duo-fen-zhi-cheng-ji-fen-ji-2
.. date: 2022-11-01 21:25:35 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text

.. code-block:: java
    :number-lines:

// Java多分支成绩分级，打乱判断条件的顺序，用并且&&连接多个条件
package xiangmu;

public class Ceshi {
	public static void main(String args[]) {
		int chengji = 85;
		if(chengji == 100) {
			dayin("满分");
		}else if(chengji >= 60 && chengji < 80) {
			dayin("及格");
		}else if(chengji >= 80 && chengji < 100) {
			dayin("优秀");
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

