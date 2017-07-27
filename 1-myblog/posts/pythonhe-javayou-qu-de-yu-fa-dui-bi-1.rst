.. title: Python和Java有趣的语法对比（1）——构造函数默认参数
.. slug: pythonhe-javayou-qu-de-yu-fa-dui-bi-1
.. date: 2017-07-27 18:15:52 UTC+08:00
.. tags: Python, java
.. category: Python
.. link: 
.. description: 
.. type: text


一直在用Python，很少用Java，现在学习Android，为了Native App的流畅性，不得不用Java了。

普通语法上，Python和Java基本可以完全对译，无非是动态类型和静态类型的区别，但是面向对象上，两者的区别就很有意思了。

今天我们来研究一下构造函数默认参数这个话题。举个例子：

如果我们想在类方法执行过程中，有时看到一些debug信息，有时不想看到，而不想每次都重复写输出语句之后再删除，该怎么办呢？

先来看看Python实现：

.. code-block :: python
    :linenos:

    class Test:

        def __init__(self, debug=False):
            self.debug = debug
            
        def test_add(self, numa, numb, debug=False):
            if self.debug or debug:
                print("test_add")
                print("numa:" + str(numa))
                print("numb:" + str(numb))
            return numa + numb

        def test_minus(self, numa, numb, debug=False):
            if self.debug or debug:
                print("test_minus")
                print("numa:" + str(numa))
                print("numb:" + str(numb))
            return numa - numb


    t = Test()
    print(t.test_add(1, 2))
    print(t.test_minus(1, 2))


输出:

::

    $ python3 test.py
    3
    -1


如果想输出一个类里的所有debug，只需要在实例化的时候设置参数就可以了。


.. code-block :: python
    :linenos:

    t = Test(debug=True)
    print(t.test_add(1, 2))
    print(t.test_minus(1, 2))


输出:

::

    $ python3 test.py
    test_add
    numa:1
    numb:2
    3
    test_minus
    numa:1
    numb:2
    -1


如果只想debug某个函数，只需要调用函数的时候设置参数就可以了。


.. code-block :: python
    :linenos:

    t = Test()
    print(t.test_add(1, 2, debug=True))
    print(t.test_minus(1, 2))


输出:

::

    $ python3 test.py
    test_add
    numa:1
    numb:2
    3
    -1


如果用Java实现类似的效果，该怎么办呢？要注意到： **Java不支持默认参数**


.. code-block :: java
    :linenos:

    public class T1{
        public static void main(String args[]){
            Test t = new Test();
            System.out.println(t.test_add(1, 2, false));
            System.out.println(t.test_minus(1, 2, false));
        }
    }

    class Test{
        boolean debug=false;
        
        void set_global(boolean debug){
            this.debug = debug;
        }
        
        int test_add(int numa, int numb, boolean debug){
            if(this.debug || debug){
                System.out.println("test_add");
                System.out.println("numa:" + numa);
                System.out.println("numb:" + numb);
            }
            return numa + numb;
        }
        
        int test_minus(int numa, int numb, boolean debug){
            if(this.debug || debug){
                System.out.println("test_minus");
                System.out.println("numa:" + numa);
                System.out.println("numb:" + numb);
            }
            return numa - numb;
        }
    }


输出:

::

    long@iphone7 MINGW64 ~/Desktop/src/test
    $ javac *.java

    long@iphone7 MINGW64 ~/Desktop/src/test
    $ java T1
    3
    -1


设置类的debug参数。

.. code-block :: java
    :linenos:

    public class T1{
        public static void main(String args[]){
            Test t = new Test();
            t.set_global(true);
            System.out.println(t.test_add(1, 2, false));
            System.out.println(t.test_minus(1, 2, false));
        }
    }


输出:

::

    long@iphone7 MINGW64 ~/Desktop/src/test
    $ javac *.java

    long@iphone7 MINGW64 ~/Desktop/src/test
    $ java T1
    test_add
    numa:1
    numb:2
    3
    test_minus
    numa:1
    numb:2
    -1



debug某个函数。

.. code-block :: java
    :linenos:

    public class T1{
        public static void main(String args[]){
            Test t = new Test();
            System.out.println(t.test_add(1, 2, true));
            System.out.println(t.test_minus(1, 2, false));
        }
    }


输出:

::

    long@iphone7 MINGW64 ~/Desktop/src/test
    $ javac *.java

    long@iphone7 MINGW64 ~/Desktop/src/test
    $ java T1
    test_add
    numa:1
    numb:2
    3
    -1


这也就意味着，由于没有默认参数机制，Java要实现这样的debug，必须要为每个函数设定一个debug参数，总不能每个方法都写一个函数重载吧？要不，就利用IDE进行一遍一遍的单步调试？？


