dp应该使用iteration，尽量优化空间不存储
#### 1.剑指offer面试题46. 把数字翻译成字符串 https://leetcode-cn.com/problemset/lcof/

利用iteration是自底向上的dp，而利用迭代（recursion）是自顶向下dp

#### 2.面试题10- I. 斐波那契数列: https://leetcode-cn.com/problems/fei-bo-na-qi-shu-lie-lcof/

```
递归法：
原理： 把 f(n)f(n) 问题的计算拆分成 f(n-1)f(n−1) 和 f(n-2)f(n−2) 两个子问题的计算，并递归，以 f(0)f(0) 和 f(1)f(1) 为终止条件。
缺点： 大量重复的递归计算，例如 f(n)f(n) 和 f(n - 1)f(n−1) 两者向下递归需要 各自计算 f(n - 2)f(n−2) 的值。
记忆化递归(可以看成没空间优化的动态规划)：
原理： 在递归法的基础上，新建一个长度为 nn 的数组，用于在递归时存储 f(0)f(0) 至 f(n)f(n) 的数字值，重复遇到某数字则直接从数组取用，避免了重复的递归计算。
缺点： 记忆化存储需要使用 O(N)O(N) 的额外空间。
动态规划：（「滚动数组」思想的递归）
原理： 以斐波那契数列性质 f(n + 1) = f(n) + f(n - 1)f(n+1)=f(n)+f(n−1) 为转移方程。
从计算效率、空间复杂度上看，动态规划是本题的最佳解法。
```
#### 3. 滑动数组法dp，节约空间

```
此处sum应该放在循环第一行，得出的是当前i对应的sum值
class Solution {
public:
    int numWays(int n) {
        if(n == 0 || n == 1){
            return 1;
        }
        int a = 1;
        int b = 1;
        int sum = 2;
        for(int i = 2; i <= n; ++i ){
            sum = (a + b) % 1000000007;
            a = b;
            b = sum;         
        }
        return sum;
    }
};
```
