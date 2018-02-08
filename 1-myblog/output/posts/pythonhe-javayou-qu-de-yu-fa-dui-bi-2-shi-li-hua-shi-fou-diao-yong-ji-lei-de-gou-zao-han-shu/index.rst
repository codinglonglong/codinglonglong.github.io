.. title: Python和Java有趣的语法对比（2）——实例化是否调用基类的构造函数
.. slug: pythonhe-javayou-qu-de-yu-fa-dui-bi-2-shi-li-hua-shi-fou-diao-yong-ji-lei-de-gou-zao-han-shu
.. date: 2017-07-27 21:10:49 UTC+08:00
.. tags: Python, java
.. category: Python
.. link: 
.. description: 
.. type: text


Python和Java在子类实例化上也有区别，看下面这个例子：

**Python版本**

.. code-block :: python
    :linenos:

    class A:
        def __init__(self):
            print("A的构造函数")
            
        def sayhello(self):
            print("Hello A")
            
    class B(A):
        def __init__(self):
            print("B的构造函数")
            
        def sayhello(self):
            print("Hello B")
            

    b = B()
    b.sayhello()
    a = A()
    a.sayhello()


输出:

::

    C:\Users\long\Desktop\src\test>python3 test.py
    B的构造函数
    Hello B
    A的构造函数
    Hello A


**Java版本**

.. code-block :: java
    :linenos:

    public class T1{
        public static void main(String args[]){
            B b =  new B();
            b.sayhello();
            A a = new A();
            a.sayhello();
        }
    }

    class A{
        A(){
            System.out.println("A的构造函数");
        }
        void sayhello(){
            System.out.println("Hello A");
        }
    }

    class B extends A{
        B(){
            System.out.println("B的构造函数");
        }
        void sayhello(){
            System.out.println("Hello B");
        }
    }


输出:

::

    C:\Users\long\Desktop\src\test>javac -encoding UTF8 *.java

    C:\Users\long\Desktop\src\test>java T1
    A的构造函数
    B的构造函数
    Hello B
    A的构造函数
    Hello A


这里体现了Java有趣的地方，对于类继承，Java实例化子类的时候，不仅会调用子类的构造函数，还会自动调用父类的构造函数，而调用子类的实例方法却不会调用父类的实例方法。在这一点上，Python比较符合人的直观感受，都是调用的实例对应的方法，不管是构造函数还是实例方法。


