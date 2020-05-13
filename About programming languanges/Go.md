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
   
   让我们来看下如何编写 Go 代码并执行它。步骤如下：

   打开编辑器如Sublime2，将以上代码添加到编辑器中。

   将以上代码保存为 hello.go

   打开命令行，并进入程序文件保存的目录中。

   输入命令 go run hello.go 并按回车执行代码。

   如果操作正确你将在屏幕上看到 "Hello World!" 字样的输出。
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

   标识符用来命名变量、类型等程序实体。一个标识符实际上就是一个或是多个字母(A~Z和a~z)数字(0~9)、下划线_组成的序列，但是第一个字符必须是字母或下划线而不能是数字。
