# Cpp
1. ```unordered_map``` 不用初始化，元素会自动初始化
2. ```stringstream fstream iostream``` 是io都可以用的
3. 数据结构中各种树总结https://www.jianshu.com/p/6f573afd2501
4. 自平衡二叉树旋转方法总结https://blog.csdn.net/saasanken/article/details/80796178
5. 红黑树旋转方法总结：维基百科  https://zh.wikipedia.org/wiki/%E7%BA%A2%E9%BB%91%E6%A0%91
6. 各种排序算法及比较https://blog.csdn.net/yushiyi6453/article/details/76407640
7. 任何```container``` 都可以用 ```.size()``` 得到长度
8. ```sliding window``` (leetcode 438 Find All Anagrams in a String 经典基础)
9. ```vector``` 重载了 ==，比较相等的时候可以直接用
10. In contaioner, ```front() back() return element, begin(), end() return iterator```
11. ```Two pointer```( leetcode 986. Interval List Intersections 经典基础）
12. 数组下标记得用```size_t```
13. ```vector emplace(iterator, args..) emplace_back(args ..)``` 调用元素相关constructor放入container中
14. ```vector``` 重载了 =， 可以用于深拷贝
15. ```
     unique_ptr<TrieNode> root;
     Trie():root(new TrieNode()) {}
    ``` 
    此指针指向的东西会自动析构 
16. c++ STL 四种智能指针https://blog.csdn.net/k346k346/article/details/81478223
