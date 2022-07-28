#### [Java刷题常用API](https://www.cnblogs.com/chzhyang/p/13494554.html)
#### [Java中ArrayList、LinkedList、Vector、Stack的比较](https://developer.51cto.com/article/605514.html)
#### [JAVA最常用容器、API详细版](https://www.i4k.xyz/article/qq_44731744/114228438#2ArrayList_214)

#### Tips
```
i & (i - 1) 将 i 的二进制形式中最右边的1变成0. i中1的个数比i & (i - 1)中1的个数多1
```
#### 为什么大家都说Java中只有值传递?
```
https://segmentfault.com/a/1190000021529503
(Integer 和 String 传入函数之后并不改变原来的值，因为 Integer a = 1 或者 String s = "abc" 都相当于在堆上new了新的变量
```

#### Math
```
1. Math.max(a,b) 取最大值
```
#### Integer
```
1. Inteter.MAX_VALUE 表示2^31 -1
```

#### String
```
1. s.length() 返回长度
2. s.charAt() 返回对应的字符
3. s.toCharArray() 返回字符串对应的字符数组
4. StringBuilder
  StringBuilder sb = new StringBuilder(1024);
  for (int i = 0; i < 1000; i++) {
      sb.append(',');
      sb.append(i);
  }
  String s = sb.toString();
```
#### Array
```
a.length array a的长度 (length is a final variable applicable for arrays. With the help of the length variable, we can obtain the size of the array. )

Arrays.asList 
The asList() method of java.util.Arrays class is used to return a fixed-size list backed by the specified array. This method acts as a bridge between array-based and collection-based APIs, in combination with Collection.toArray(). The returned list is serializable and implements RandomAccess.
            // Creating Arrays of String type
            String a[]
                = new String[] { "A", "B", "C", "D" };
            // Getting the list view of Array
            List<String> list = Arrays.asList(a);
            也可以 Arrays.asList("A", "B", "C", "D");


Arrays.sort(a); 给array a排序
If you use an Integer[] instead of int[], then you can pass a Comparator as 2nd argument to the sort method. To impose reverse ordering, you can make use of Collections.reverseOrder() method:
Arrays.sort(arr, Collections.reverseOrder());

java 在声明了一个数组，并为其分配好存储空间后，未赋值之前会默认对其初始化：
整形数组 默认初始值为0；
布尔数组默认初始值为 false；
String 数组以及 对象数组初始值为 null.
```
