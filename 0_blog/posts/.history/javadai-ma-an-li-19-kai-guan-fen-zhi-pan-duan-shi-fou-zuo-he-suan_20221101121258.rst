.. title: Java代码案例19——开关分支判断是否做核酸
.. slug: javadai-ma-an-li-19-kai-guan-fen-zhi-pan-duan-shi-fou-zuo-he-suan
.. date: 2022-11-01 22:09:56 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text

.. code-block:: java
    :number-lines:

// Java开关分支判断是否做核酸
// 每周一、四、六常态化核酸
package xiangmu;

public class Ceshi {
	public static void main(String args[]) {
		int xingqi = 4;
		switch(xingqi) {
			case 1: 
			case 4: 
			case 6: 
				dayin("今天做核酸");
				break;
			default: 
				dayin("今天不做核酸");
		}
	}
	public static void dayin(String zifuchuan) {
		System.out.println(zifuchuan);
	}
}





.. code-block:: text

    今天做核酸


