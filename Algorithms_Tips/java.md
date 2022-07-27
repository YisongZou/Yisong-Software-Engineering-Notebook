```为什么大家都说Java中只有值传递?```
https://segmentfault.com/a/1190000021529503

```Integer```
1. Inteter.MAX_VALUE 表示2^31 -1


```String```
1. s.length() 返回长度
2. s.charAt() 返回对应的字符
3. StringBuilder
  StringBuilder sb = new StringBuilder(1024);
  for (int i = 0; i < 1000; i++) {
      sb.append(',');
      sb.append(i);
  }
  String s = sb.toString();
