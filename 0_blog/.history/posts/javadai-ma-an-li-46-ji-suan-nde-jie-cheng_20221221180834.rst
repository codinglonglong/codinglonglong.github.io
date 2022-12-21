.. title: Java代码案例46——计算n的阶乘
.. slug: javadai-ma-an-li-46-ji-suan-nde-jie-cheng
.. date: 2022-12-21 23:06:38 UTC+08:00
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
		// 给定正整数n，计算n的阶乘
		// n的阶乘 n! = 1 * 2 * 3 * ... * (n-1) * n
		// 5! = 1 * 2 * 3 * 4 * 5
		int n = 5;
		// 如果是计算连加，变量jieguo初始值是0
		// 如果是计算连乘，变量jieguo初始值是1
		int jieguo = 1;  
		for(int m = 1; m <= n; m = m + 1) {
			jieguo = jieguo * m;
		}
		System.out.println(n + "! = " + jieguo);
	}
}


.. code-block:: text

    5! = 120
