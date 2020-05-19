1. ### Udemy course:
   ```
      Learn How To Code: Google's Go (golang) Programming Language
    ```
https://www.udemy.com/course/learn-how-to-code/learn/lecture/3993384?start=0#overview

2. 菜鸟教程：https://www.runoob.com/go/go-tutorial.html
3. 需要注意的是 { 不能单独放在一行，所以以下代码在运行时会产生错误：
```
package main

import "fmt"

func main()  
{  // 错误，{ 不能在单独的行上
    fmt.Println("Hello, World!")
}
```

4. 执行 Go 程序
   ```
   让我们来看下如何编写 Go 代码并执行它。步骤如下：

   打开编辑器如Sublime2，将以上代码添加到编辑器中。

   将以上代码保存为 hello.go

   打开命令行，并进入程序文件保存的目录中。

   输入命令 go run hello.go 并按回车执行代码。

   如果操作正确你将在屏幕上看到 "Hello World!" 字样的输出。
   ```
```
$ go run hello.go
Hello, World!
```
   我们还可以使用 go build 命令来生成二进制文件：
```
$ go build hello.go 
$ ls
hello    hello.go
$ ./hello 
Hello, World!
```
5. 标识符
```
   标识符用来命名变量、类型等程序实体。一个标识符实际上就是一个或是多个字母(A-Z和a-z)数字(0-9)、下划线_组成的序列，但是第一个字符必须是字母或下划线而不能是数字。
```
6. 变量

```
这种不带声明格式的只能在函数体中出现
g, h := 123, "hello"
```
```
a, b, c := 5, 7, "abc"
右边的这些值以相同的顺序赋值给左边的变量，所以 a 的值是 5， b 的值是 7，c 的值是 "abc"。

这被称为 并行 或 同时 赋值。

如果你想要交换两个变量的值，则可以简单地使用 a, b = b, a，两个变量的类型必须是相同。

空白标识符 _ 也被用于抛弃值，如值 5 在：_, b = 5, 7 中被抛弃。

_ 实际上是一个只写变量，你不能得到它的值。这样做是因为 Go 语言中你必须使用所有被声明的变量，但有时你并不需要使用从一个函数得到的所有返回值。

并行赋值也被用于当一个函数返回多个返回值时，比如这里的 val 和错误 err 是通过调用 Func1 函数同时得到：val, err = Func1(var1)。
```
7. 条件语句
```
Go 没有三目运算符，所以不支持 ?: 形式的条件判断。
```
8. 函数
```
func function_name( [parameter list] ) [return_types] {
   函数体
}

func：函数由 func 开始声明
function_name：函数名称，函数名和参数列表一起构成了函数签名。
parameter list：参数列表，参数就像一个占位符，当函数被调用时，你可以将值传递给参数，这个值被称为实际参数。参数列表指定的是参数类型、顺序、及参数个数。参数是可选的，也就是说函数也可以不包含参数。
return_types：返回类型，函数返回一列值。return_types 是该列值的数据类型。有些功能不需要返回值，这种情况下 return_types 不是必须的。
函数体：函数定义的代码集合。
```

```
函数返回多个值
Go 函数可以返回多个值，例如：

实例
package main

import "fmt"

func swap(x, y string) (string, string) {
   return y, x
}

func main() {
   a, b := swap("Google", "Runoob")
   fmt.Println(a, b)
}
以上实例执行结果为：

Runoob Google
```

```
引用传递是指在调用函数时将实际参数的地址传递到函数中，那么在函数中对参数所进行的修改，将影响到实际参数。

引用传递指针参数传递到函数内，以下是交换函数 swap() 使用了引用传递：

/* 定义交换值函数*/
swap(&a, &b)
func swap(x *int, y *int) {
   var temp int
   temp = *x    /* 保持 x 地址上的值 */
   *x = *y      /* 将 y 值赋给 x */
   *y = temp    /* 将 temp 值赋给 y */
}
```
```
Go 没有面向对象，而我们知道常见的 Java。

C++ 等语言中，实现类的方法做法都是编译器隐式的给函数加一个 this 指针，而在 Go 里，这个 this 指针需要明确的申明出来，其实和其它 OO 语言并没有很大的区别。

在 C++ 中是这样的:

class Circle {
  public:
    float getArea() {
       return 3.14 * radius * radius;
    }
  private:
    float radius;
}

// 其中 getArea 经过编译器处理大致变为
float getArea(Circle *const c) {
  ...
}
在 Go 中则是如下:

func (c Circle) getArea() float64 {
  //c.radius 即为 Circle 类型对象中的属性
  return 3.14 * c.radius * c.radius
}
```
9. 数组
```
声明数组
Go 语言数组声明需要指定元素类型及元素个数，语法格式如下：

var variable_name [SIZE] variable_type
以上为一维数组的定义方式。例如以下定义了数组 balance 长度为 10 类型为 float32：

var balance [10] float32
初始化数组
以下演示了数组初始化：

var balance = [5]float32{1000.0, 2.0, 3.4, 7.0, 50.0}
初始化数组中 {} 中的元素个数不能大于 [] 中的数字。

如果忽略 [] 中的数字不设置数组大小，Go 语言会根据元素的个数来设置数组的大小：

 var balance = [...]float32{1000.0, 2.0, 3.4, 7.0, 50.0}
该实例与上面的实例是一样的，虽然没有设置数组的大小。

 balance[4] = 50.0
 ```
 10. 指针
 ```
 Go 空指针
当一个指针被定义后没有分配到任何变量时，它的值为 nil。

nil 指针也称为空指针。

nil在概念上和其它语言的null、None、nil、NULL一样，都指代零值或空值。

一个指针变量通常缩写为 ptr。
```
