```
All of programming
```
https://play.google.com/books/reader?id=-zViCgAAQBAJ&pg=GBS.PA617.w.5.0.58

### 1 
```
https://en.wikipedia.org/wiki/Polymorphism_(computer_science)

多态相关

函数重载属于一种多态，叫做特设多态（Ad hoc polymorphism）。特设多态的意思是，一个函数有，
有限数量的多种不同的实现，依赖参数的类型来选择调用特定版本的函数实现。这种选择在编译期就可以判断，
所以称为静态多态。 而多态是更一般的概念，不同的类型有相同的接口，就叫做多态。还有两者常见的多态，
参数多态和包含多态。

参数多态就是定义类型时候，或者某个类型的实现时候（比如类，函数，变量等）保留类型参数，
等以后在使用时候，由程序员或者编译器补上适当的类型参数。有时候也会被叫做泛型编程。一般这也是编译期决定的，
也是静态多态 

包含多态：B 是 A 的子类型（分为名义子类型和结构子类型，名义子类型就是必须显式声明子类型关系，
结构子类型就是只要满足接口一致就自动实现了子类型关系），所有使用 A 的地方我们都可以用 B 去安全替换上 
。包含多态就是，同样的操作，我们可以作用于 A 和  A 的所有子类型（比如B）上。在包含多态中，
由于值是不定类型的，可能是任何的子类型，实现也可能是任意子类型中配套的任意实现，我们编译期拿不到足够的信息，
所以需要运行时通过动态分派查找具体的类型对应的实现，所以包含多态是动态多态。在好多语言中，
为了凸现这个参数要动态分派，我们会把它放到点号前面，比如 foo.make('zhihu') 中的 foo
```

```
虚函数是C++中用于实现多态(polymorphism)的机制。核心理念就是通过基类访问派生类定义的函数。
```

### 2. C++中public、protected、private继承的区别
```
https://blog.csdn.net/qq_42475914/article/details/94590210?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-2.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-2.control

https://blog.csdn.net/qq583083658/article/details/80740299
```

### 3. C/C++---static函数，static成员函数，static变量，static成员变量 再来理一理
https://blog.csdn.net/FreeApe/article/details/50979425
