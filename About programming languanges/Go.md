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
```
