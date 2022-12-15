.. title: Java中do...while结构应用场景探究
.. slug: javazhong-dowhilejie-gou-ying-yong-chang-jing-tan-jiu
.. date: 2022-12-16 01:05:36 UTC+08:00
.. tags: Java探究
.. category: Java
.. link: 
.. description: 
.. type: text

本文针对如下业务流程的实现方法进行了探究。

1. 检测用户是否已登录，未登录则退出系统

2. 检测题库名是否有效，无效则退出系统

3. 检测考试是否还有时间，没有时间则退出系统

4. 答题，正常退出系统

对比了【多层嵌套分支法】、【标志变量法】和【do...while(false)循环法】，深刻体现了do...while结构在此类业务流程中的巧妙之处。

.. TEASER_END

.. code-block:: java
    :number-lines:

    package xiangmu;

    public class Ceshi {
        public static void main(String args[]) {
            // 写法1：多层嵌套分支
            // 如果需要完成的检测函数很多，那么if分支的嵌套层次就会很多
            String yhm = "Tom";
            String tkm = "Java期末考试";
            double sj = 100;
            if(jiance_yonghudenglu(yhm)) {
                if(jiance_tikuyouxiao(tkm)) {
                    if(jiance_shijian(sj)) {
                        dati();
                    }else {
                        System.out.println("考试时间已用完！");
                    }
                }else {
                    System.out.println("题库名无效！");
                }
            }else {
                System.out.println("用户未登录！");
            }
            System.out.println("退出系统！");
        }
        public static boolean jiance_yonghudenglu(String yonghuming) {
            // 检测用户是否已登录，已登录返回true，未登录返回false
            return true;
        }
        public static boolean jiance_tikuyouxiao(String tikuming) {
            // 检测题库名是否有效，有效返回true，无效返回false
            return true;
        }
        public static boolean jiance_shijian(double shijian) {
            // 检测考试是否还有时间，有时间返回true，没有时间返回false
            return true;
        }
        public static void dati() {
            // 答题
            System.out.println("答题");
        }
    }


.. code-block:: java
    :number-lines:

    package xiangmu;

    public class Ceshi {
        public static void main(String args[]) {
            // 写法2：标志变量法
            // 这样写不需要多层嵌套，但不管之前的检测函数是否通过，后续的每一个检测函数都需要执行
            String yhm = "Tom";
            String tkm = "Java期末考试";
            double sj = 100;
            int biaozhi = 0;
            if(!jiance_yonghudenglu(yhm)) {    // !true == false    !false == true
                System.out.println("用户未登录！");
                biaozhi = 1;
            }
            if(!jiance_tikuyouxiao(tkm)) {
                System.out.println("题库名无效！");
                biaozhi = 1;
            }
            if(!jiance_shijian(sj)) {
                System.out.println("考试时间已用完！");
                biaozhi = 1;
            }
            if(biaozhi == 0) {
                dati();
            }
            System.out.println("退出系统！");
        }
        public static boolean jiance_yonghudenglu(String yonghuming) {
            // 检测用户是否已登录，已登录返回true，未登录返回false
            return true;
        }
        public static boolean jiance_tikuyouxiao(String tikuming) {
            // 检测题库名是否有效，有效返回true，无效返回false
            return true;
        }
        public static boolean jiance_shijian(double shijian) {
            // 检测考试是否还有时间，有时间返回true，没有时间返回false
            return true;
        }
        public static void dati() {
            // 答题
            System.out.println("答题");
        }
    }


.. code-block:: java
    :number-lines:

    package xiangmu;

    public class Ceshi {
        public static void main(String args[]) {
            // 写法3：do...while(false)循环法
            // 不需要多层if嵌套，只要有一个检测函数不通过，其他检测函数直接被跳过
            // 既实现了减少代码嵌套层次，又保证了执行效率
            // 巧妙！！！
            String yhm = "Tom";
            String tkm = "Java期末考试";
            double sj = 100;
            do {
                if(!jiance_yonghudenglu(yhm)) {       // !true == false    !false == true
                    System.out.println("用户未登录！");
                    break;
                }
                if(!jiance_tikuyouxiao(tkm)) {
                    System.out.println("题库名无效！");
                    break;
                }
                if(!jiance_shijian(sj)) {
                    System.out.println("考试时间已用完！");
                    break;
                }
                dati();
            }while(false);
            System.out.println("退出系统！");
        }
        public static boolean jiance_yonghudenglu(String yonghuming) {
            // 检测用户是否已登录，已登录返回true，未登录返回false
            return true;
        }
        public static boolean jiance_tikuyouxiao(String tikuming) {
            // 检测题库名是否有效，有效返回true，无效返回false
            return true;
        }
        public static boolean jiance_shijian(double shijian) {
            // 检测考试是否还有时间，有时间返回true，没有时间返回false
            return true;
        }
        public static void dati() {
            // 答题
            System.out.println("答题");
        }
    }
