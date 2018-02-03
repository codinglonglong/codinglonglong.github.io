.. title: Java带包编译源文件
.. slug: javadai-bao-bian-yi-yuan-wen-jian
.. date: 2017-07-22 14:44:00 UTC+08:00
.. tags: java, package
.. category: Java
.. link: 
.. description: 
.. type: text


如果在java代码中给出package，直接编译生成的class文件会无法运行，提示 **“错误: 找不到或无法加载主类”** 。

目录结构：

::

    Desktop/src/test/T1.java
    Desktop/src/test/T1.class


解决办法如下：

.. code-block :: java
    :linenos:

    package src;
    public class T1{
        public static void main(String args[]){
            System.out.println("Hello World");
        }
    }


::

    >> long@iphone7 MINGW64 ~/Desktop
    >> $ javac -d . src/test/T1.java

    >> long@iphone7 MINGW64 ~/Desktop
    >> $ java src.T1
    >> Hello World


