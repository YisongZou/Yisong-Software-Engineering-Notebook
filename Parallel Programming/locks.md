### 多线程中的各种锁

https://www.zhihu.com/question/66733477


### 死锁例子

https://blog.csdn.net/xiaoye319/article/details/87376963

### For Understanding of deadlock

```
For deadlock, the two or more threads can run the same code or the different code,
this does not matter. However they are contesting on the same resources.
For example there are two resource A and B.
Thread1:
Lock(A)
Lock(B)

Thread2:
Lock(B)
Lock(A)

The stuff above will cause dead lock because the two threads are contesting on the resources in reverse order
```
