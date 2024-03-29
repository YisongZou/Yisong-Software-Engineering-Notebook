### public private 继承

https://blog.csdn.net/eric_4300741/article/details/52851590

### Collection Hierarchy in java
https://www.scientecheasy.com/2020/09/collection-hierarchy-in-java.html/
![Java Hierarchy](https://github.com/YisongZou/Yisong-Software-Engineering-Notebook/blob/master/About%20programming%20languanges/%E6%88%AA%E5%B1%8F2021-02-03%20%E4%B8%8B%E5%8D%8812.19.15.png)
e-extends i-implements

![](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20210315172345/Java-Collections-Framework-Hierarchy.png)

### 继承转型 参考：[廖雪峰](https://www.liaoxuefeng.com/wiki/1252599548343744/1260454548196032)  廖雪峰java教程-面向对象编程-面向对象基础-继承
```
向上转型
如果一个引用变量的类型是Student，那么它可以指向一个Student类型的实例：

Student s = new Student();
如果一个引用类型的变量是Person，那么它可以指向一个Person类型的实例：

Person p = new Person();
现在问题来了：如果Student是从Person继承下来的，那么，一个引用类型为Person的变量，能否指向Student类型的实例？

Person p = new Student(); // ???
测试一下就可以发现，这种指向是允许的！

这是因为Student继承自Person，因此，它拥有Person的全部功能。Person类型的变量，如果指向Student类型的实例，对它进行操作，是没有问题的！

这种把一个子类类型安全地变为父类类型的赋值，被称为向上转型（upcasting）。

向上转型实际上是把一个子类型安全地变为更加抽象的父类型：

Student s = new Student();
Person p = s; // upcasting, ok
Object o1 = p; // upcasting, ok
Object o2 = s; // upcasting, ok
注意到继承树是Student > Person > Object，所以，可以把Student类型转型为Person，或者更高层次的Object。

向下转型
和向上转型相反，如果把一个父类类型强制转型为子类类型，就是向下转型（downcasting）。例如：

Person p1 = new Student(); // upcasting, ok
Person p2 = new Person();
Student s1 = (Student) p1; // ok
Student s2 = (Student) p2; // runtime error! ClassCastException!
如果测试上面的代码，可以发现：

Person类型p1实际指向Student实例，Person类型变量p2实际指向Person实例。在向下转型的时候，把p1转型为Student会成功，因为p1确实指向Student实例，把p2转型为Student会失败，因为p2的实际类型是Person，不能把父类变为子类，因为子类功能比父类多，多的功能无法凭空变出来。

因此，向下转型很可能会失败。失败的时候，Java虚拟机会报ClassCastException。

为了避免向下转型出错，Java提供了instanceof操作符，可以先判断一个实例究竟是不是某种类型：

Person p = new Person();
System.out.println(p instanceof Person); // true
System.out.println(p instanceof Student); // false

Student s = new Student();
System.out.println(s instanceof Person); // true
System.out.println(s instanceof Student); // true

Student n = null;
System.out.println(n instanceof Student); // false
instanceof实际上判断一个变量所指向的实例是否是指定类型，或者这个类型的子类。如果一个引用变量为null，那么对任何instanceof的判断都为false。

利用instanceof，在向下转型前可以先判断：

Person p = new Student();
if (p instanceof Student) {
    // 只有判断成功才会向下转型:
    Student s = (Student) p; // 一定会成功
}
从Java 14开始，判断instanceof后，可以直接转型为指定变量，避免再次强制转型。例如，对于以下代码：

Object obj = "hello";
if (obj instanceof String) {
    String s = (String) obj;
    System.out.println(s.toUpperCase());
}
可以改写如下：

// instanceof variable:
public class Main {
    public static void main(String[] args) {
        Object obj = "hello";
        if (obj instanceof String s) {
            // 可以直接使用变量s:
            System.out.println(s.toUpperCase());
        }
    }
}

 ```
 
 ### Java 包
 https://www.runoob.com/java/java-package.html
 
 
### abstract class和interface的区别
https://www.jianshu.com/p/cbffaf7e7c42

https://blog.csdn.net/b271737818/article/details/3950245


### java中的经典问题：传值与传引用
https://blog.csdn.net/jiangnan2014/article/details/22944075
```
1.传递的参数“值” 会在 函数当前运行栈上 复制一份。所有的 操作和赋值 都是对那个 参数“值”副本 进行的。操作能够 改变成员变量，因为参数“值”副本 是一个 地址，能够正确指向成员变量的位置。而赋值 则根本没用，因为只是改变了当前函数栈内 参数“值”副本 的内容，而没有改变上一层函数栈内的 对应“值”;

2.=和.
=（等号）操作的是变量的值；

.（句点）操作的是引用的值；
3.关于传参的问题只要把栈和堆搞明白了就应该很容易理解了：

java传参都是传值，也就是把栈里面的值复制一份传给参数；
当然如果是原始类型就是栈内原始类型值复制了一份传递；
如果是对象或者数组这样的引用类型，那么栈里面的值就是该对象的引用的值具体说就是地址了，把这个值复制一份传给方法，也就是复制了一个引用给方法去使用；
```
