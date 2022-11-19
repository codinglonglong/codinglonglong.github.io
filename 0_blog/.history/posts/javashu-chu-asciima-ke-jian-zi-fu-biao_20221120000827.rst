.. title: Java输出ASCII码可见字符表
.. slug: javashu-chu-asciima-ke-jian-zi-fu-biao
.. date: 2022-11-19 23:18:29 UTC+08:00
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
        char a = 1;
        for(a = 32;a<127;a++) {
        	System.out.print(String.format("%5d", (int)a)+"\t");
        	System.out.print(a+"\t");
        	if((a-31) % 6 == 0) {
        		System.out.println();
        	}
        }
    }
}

.. image:: /images/ec1f2d6a6c4fe3de57c90f765477408.png