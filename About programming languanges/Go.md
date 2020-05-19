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
11. 结构体
```
package main

import "fmt"

type Books struct {
   title string
   author string
   subject string
   book_id int
}


func main() {

    // 创建一个新的结构体
    fmt.Println(Books{"Go 语言", "www.runoob.com", "Go 语言教程", 6495407})

    // 也可以使用 key => value 格式
    fmt.Println(Books{title: "Go 语言", author: "www.runoob.com", subject: "Go 语言教程", book_id: 6495407})

    // 忽略的字段为 0 或 空
   fmt.Println(Books{title: "Go 语言", author: "www.runoob.com"})
}
```
```
结构体指针
你可以定义指向结构体的指针类似于其他指针变量，格式如下：

var struct_pointer *Books
以上定义的指针变量可以存储结构体变量的地址。查看结构体变量地址，可以将 & 符号放置于结构体变量前：

struct_pointer = &Book1
使用结构体指针访问结构体成员，使用 "." 操作符：

struct_pointer.title
```
12. 切片（slice）
```
Go 语言切片(Slice)
Go 语言切片是对数组的抽象。

Go 数组的长度不可改变，在特定场景中这样的集合就不太适用，Go中提供了一种灵活，功能强悍的内置类型切片("动态数组"),与数组相比切片的长度是不固定的，可以追加元素，在追加时可能使切片的容量增大。

定义切片
你可以声明一个未指定大小的数组来定义切片：

var identifier []type
切片不需要说明长度。

或使用make()函数来创建切片:

var slice1 []type = make([]type, len)

也可以简写为

slice1 := make([]type, len)
也可以指定容量，其中capacity为可选参数。

make([]T, length, capacity)
这里 len 是数组的长度并且也是切片的初始长度。

切片初始化
s :=[] int {1,2,3 } 
直接初始化切片，[]表示是切片类型，{1,2,3}初始化值依次是1,2,3.其cap=len=3

s := arr[:] 
初始化切片s,是数组arr的引用

s := arr[startIndex:endIndex] (右下标不包含）
将arr中从下标startIndex到endIndex-1 下的元素创建为一个新的切片

s := arr[startIndex:] 
默认 endIndex 时将表示一直到arr的最后一个元素

s := arr[:endIndex] 
默认 startIndex 时将表示从arr的第一个元素开始

s1 := s[startIndex:endIndex] 
通过切片s初始化切片s1

s :=make([]int,len,cap) 
通过内置函数make()初始化切片s,[]int 标识为其元素类型为int的切片
```
```
len() 和 cap() 函数
切片是可索引的，并且可以由 len() 方法获取长度。

切片提供了计算容量的方法 cap() 可以测量切片最长可以达到多少。
```
```
空(nil)切片
一个切片在未初始化之前默认为 nil，长度为 0
```
```
切片截取
可以通过设置下限及上限来设置截取切片 [lower-bound:upper-bound]，实例如下：

实例
package main

import "fmt"

func main() {
   /* 创建切片 */
   numbers := []int{0,1,2,3,4,5,6,7,8}  
   printSlice(numbers)

   /* 打印原始切片 */
   fmt.Println("numbers ==", numbers)

   /* 打印子切片从索引1(包含) 到索引4(不包含)*/
   fmt.Println("numbers[1:4] ==", numbers[1:4])

   /* 默认下限为 0*/
   fmt.Println("numbers[:3] ==", numbers[:3])

   /* 默认上限为 len(s)*/
   fmt.Println("numbers[4:] ==", numbers[4:])

   numbers1 := make([]int,0,5)
   printSlice(numbers1)

   /* 打印子切片从索引  0(包含) 到索引 2(不包含) */
   number2 := numbers[:2]
   printSlice(number2)

   /* 打印子切片从索引 2(包含) 到索引 5(不包含) */
   number3 := numbers[2:5]
   printSlice(number3)

}

func printSlice(x []int){
   fmt.Printf("len=%d cap=%d slice=%v\n",len(x),cap(x),x)
}
执行以上代码输出结果为：

len=9 cap=9 slice=[0 1 2 3 4 5 6 7 8]
numbers == [0 1 2 3 4 5 6 7 8]
numbers[1:4] == [1 2 3]
numbers[:3] == [0 1 2]
numbers[4:] == [4 5 6 7 8]
len=0 cap=5 slice=[]
len=2 cap=9 slice=[0 1]
len=3 cap=7 slice=[2 3 4]
```
```
append() 和 copy() 函数
如果想增加切片的容量，我们必须创建一个新的更大的切片并把原分片的内容都拷贝过来。

下面的代码描述了从拷贝切片的 copy 方法和向切片追加新元素的 append 方法。

实例
package main

import "fmt"

func main() {
   var numbers []int
   printSlice(numbers)

   /* 允许追加空切片 */
   numbers = append(numbers, 0)
   printSlice(numbers)

   /* 向切片添加一个元素 */
   numbers = append(numbers, 1)
   printSlice(numbers)

   /* 同时添加多个元素 */
   numbers = append(numbers, 2,3,4)
   printSlice(numbers)

   /* 创建切片 numbers1 是之前切片的两倍容量*/
   numbers1 := make([]int, len(numbers), (cap(numbers))*2)

   /* 拷贝 numbers 的内容到 numbers1 */
   copy(numbers1,numbers)
   printSlice(numbers1)  
}

func printSlice(x []int){
   fmt.Printf("len=%d cap=%d slice=%v\n",len(x),cap(x),x)
}
以上代码执行输出结果为：

len=0 cap=0 slice=[]
len=1 cap=1 slice=[0]
len=2 cap=2 slice=[0 1]
len=5 cap=6 slice=[0 1 2 3 4]
len=5 cap=12 slice=[0 1 2 3 4]
```
13. Range
```
Go 语言范围(Range)
Go 语言中 range 关键字用于 for 循环中迭代数组(array)、切片(slice)、通道(channel)或集合(map)的元素。在数组和切片中它返回元素的索引和索引对应的值，在集合中返回 key-value 对。

实例
实例
package main
import "fmt"
func main() {
    //这是我们使用range去求一个slice的和。使用数组跟这个很类似
    nums := []int{2, 3, 4}
    sum := 0
    for _, num := range nums {
        sum += num
    }
    fmt.Println("sum:", sum)
    //在数组上使用range将传入index和值两个变量。上面那个例子我们不需要使用该元素的序号，所以我们使用空白符"_"省略了。有时侯我们确实需要知道它的索引。
    for i, num := range nums {
        if num == 3 {
            fmt.Println("index:", i)
        }
    }
    //range也可以用在map的键值对上。
    kvs := map[string]string{"a": "apple", "b": "banana"}
    for k, v := range kvs {
        fmt.Printf("%s -> %s\n", k, v)
    }
    //range也可以用来枚举Unicode字符串。第一个参数是字符的索引，第二个是字符（Unicode的值）本身。
    for i, c := range "go" {
        fmt.Println(i, c)
    }
}
以上实例运行输出结果为：

sum: 9
index: 1
a -> apple
b -> banana
0 103
1 111
```
14. 
