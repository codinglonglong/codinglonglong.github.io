.. title: Java代码案例25——基本数据类型的自动类型转换
.. slug: javadai-ma-an-li-25-ji-ben-shu-ju-lei-xing-de-zi-dong-lei-xing-zhuan-huan
.. date: 2022-11-14 22:19:53 UTC+08:00
.. tags: Java代码案例
.. category: Java
.. link: 
.. description: 
.. type: text



    // Java基本数据类型的自动类型转换

    package xiangmu;

    public class Ceshi {
        public static void main(String args[]) {
            // byte、short、char三种类型的变量，运算过程中会自动转成int类型
            // 赋值直接给整数，Java默认按int类型
            // 赋值直接给小数，Java默认按double类型
            // 自动转换按照 int => long => float => double 的顺序
            // 具体案例看以下代码
            byte a = 1;
            dayin("1. " + getType(a));
            dayin("2. " + getType(a + 1));
            short b = 1;
            dayin("3. " + getType(b));
            dayin("4. " + getType(b + 1));
            char c = 'a';
            dayin("5. " + getType(c));
            dayin("6. " + getType(c + 1));
            int d = 1;
            dayin("7. " + getType(d));
            dayin("8. " + getType(d + 1));
            // 定义long型变量，需要在赋值结尾加字母l
            // 这里没有加结尾字母l，是因为Java默认做了类型转换，把int型的1，换成了long型的1
            // int型和long型都可以存下1，所以没有问题
            long e = 1;
            dayin("9. " + getType(e));
            dayin("10. " + getType(e + 1));
            // 没有结尾字母l，这里会报错，因为123456789123456789超过了int的上限
            // 不加字母l，Java默认将123456789123456789按int处理，存不下
            long f = 123456789123456789l;
            dayin("11. " + getType(f));
            dayin("12. " + getType(f + 1));
            // 定义float型变量，需要在赋值结尾加字母f
            // 这里没有加字母f，是因为Java默认做了类型转换，把int型的i，换成了float型的1.0
            float g = 1;
            dayin("13. " + getType(g));
            dayin("14. " + getType(g + 1));
            // 没有结尾字母f，这里会报错，因为Java默认将小数按double类型处理
            // 而double类型范围大于float类型，无法自动转换。
            float h = 1.5f;
            dayin("15. " + getType(h));
            dayin("16. " + getType(h + 1));
            double i = 1.2;
            dayin("17. " + getType(i));
            dayin("18. " + getType(i + 1));
            // 以下为混合运算
            // byte和short运算，得到int类型
            dayin("19. " + getType(a + b));
            // short和char运算，得到int类型
            dayin("20. " + getType(b + c));
            // int和long运算，得到long类型
            dayin("21. " + getType(d + e));
            // int和float运算，得到float类型
            dayin("22. " + getType(d + g));
            // long和float运算，得到float类型
            dayin("23. " + getType(e + g));
            // int和double运算，得到double类型
            dayin("24. " + getType(d + i));
            // long和double运算，得到double类型
            dayin("25. " + getType(e + i));
            // float和double运算，得到double类型
            dayin("26. " + getType(g + i));    	
            // 所以 9/5 的结果是整数1，因为9默认是int类型，5默认是int类型，运算结果也是int类型
            dayin("9 / 5 = " + 9/5 + "  " + getType(9/5));
            // 而 9.0/5 的结果是1.8，因为9.0默认是double类型，5默认是int类型，运算结果是double类型
            dayin("9.0 / 5 = " + 9.0/5 + "  " + getType(9.0/5));
            // 如果做强制类型转换成float，也就是 (float)9/5，那么9被强制转换成了float类型，5默认是int类型，运算结果是float类型
            dayin("(float)9 / 5 = " + (float)9/5 + "  " + getType((float)9/5));
        }
        public static String getType(Object obj) {
            // 此函数用于输出变量类型名
            return obj.getClass().toString();
        }
        public static void dayin(Object obj) {
            System.out.println(obj);
        }
    }
