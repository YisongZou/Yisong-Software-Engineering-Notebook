# Cpp
### STL比较好的总结：https://www.cnblogs.com/skyfsm/p/6934246.html
1. ```unordered_map``` 直接map[key] = value即可， 而vector等如果相应元素没初始化，需要用push_back();
2. ```stringstream fstream iostream``` 是io都可以用的
3. 数据结构中各种树总结https://www.jianshu.com/p/6f573afd2501
4. 自平衡二叉树旋转方法总结https://blog.csdn.net/saasanken/article/details/80796178
5. 红黑树旋转方法总结：维基百科  https://zh.wikipedia.org/wiki/%E7%BA%A2%E9%BB%91%E6%A0%91
6. 各种排序算法及比较https://blog.csdn.net/yushiyi6453/article/details/76407640
7. 任何```container``` 都可以用 ```.size()``` 得到长度
8. ```sliding window``` (leetcode 438 Find All Anagrams in a String 经典基础)
9. ```vector``` 重载了 ==，比较相等的时候可以直接用```vector``` 重载了 =， 可以用于深拷贝
10. In container, ```front() back() return a reference to the element, begin(), end() return iterator, 
 pop() Removes the element on top, top() Returns a reference to the top element```

   ##### (1)vector:
```
push_back(), pop_back(), begin(), end(), front(), back();

erase():
iterator erase (const_iterator position); 
iterator erase (const_iterator first, const_iterator last);
Removes from the vector either a single element (position) or a range of elements([first,last)).

clear(): Removes all elements from the vector (which are destroyed),
leaving the container with a size of 0.

emplace():
emplace(iterator, args..) emplace_back(args ..) 调用元素相关constructor放入container中
Construct and insert element
The container is extended by inserting a new element at position. This new element is 
constructed in place using args as the arguments for its construction.
This effectively increases the container size by one.
An automatic reallocation of the allocated storage space happens if -and only if- the
new vector size surpasses the current vector capacity.
```

   ##### (2)string:
```
std::string::operator+=
C++98C++11
string (1)	
string& operator+= (const string& str);
c-string (2)	
string& operator+= (const char* s);
character (3)	
string& operator+= (char c);
initializer list (4)	
string& operator+= (initializer_list<char> il);
```
```
push_back(char c), pop_back()(the last character), begin(), end(), front(), back();

erase():
sequence (1)	string& erase (size_t pos = 0, size_t len = npos);
character (2) iterator erase (const_iterator p);
range (3)	iterator erase (const_iterator first, const_iterator last);
(1) sequence
Erases the portion of the string value that begins at the character position pos and spans 
len characters (or until the end of the string, if either the content is too short or if 
len is string::npos.
Notice that the default argument erases all characters in the string (like member function clear).
(2) character
Erases the character pointed by p.
(3) range
Erases the sequence of characters in the range [first,last).

find():
Searches the string for the first occurrence of the sequence specified by its arguments.
When pos is specified, the search only includes characters at or after position pos, 
ignoring any possible occurrences that include characters before pos.
string (1)	size_t find (const string& str, size_t pos = 0) const noexcept;
c-string (2)	size_t find (const char* s, size_t pos = 0) const;
buffer (3)	size_t find (const char* s, size_t pos, size_type n) const;
character (4)	size_t find (char c, size_t pos = 0) const noexcept;

substr():
string substr (size_t pos = 0, size_t len = npos) const;
Generate substring
Returns a newly constructed string object with its value initialized to a copy of 
a substring of this object.
The substring is the portion of the object that starts at character position pos 
and spans len characters (or until the end of the string, whichever comes first).
```

   ##### (3)stack: 
```
top(); push(); pop();
```
   ##### (4)queue:
```
front(); back(); push(); pop();
```
   ##### (5)unordered_map: 
```
begin(); end(); 

count(): 
Searches the container for elements whose key is k and returns the number of elements found. 
Because unordered_map containers do not allow for duplicate keys, this means that the function actually
returns 1 if an element with that key exists in the container, and zero otherwise.
```

11. ```Two pointer```( leetcode 986. Interval List Intersections 经典基础）
12. 数组下标记得用```size_t```
13. ```
     unique_ptr<TrieNode> root;
     Trie():root(new TrieNode()) {}
    ``` 
    此指针指向的东西会自动析构 
14. c++ STL 四种智能指针https://blog.csdn.net/k346k346/article/details/81478223
15. c++ map与unordered_map区别及使用 https://blog.csdn.net/BillCYJ/article/details/78985895 
16. 自定义sort:
 ```
 class Solution {
public:
    int twoCitySchedCost(vector<vector<int>>& costs) {
        sort(costs.begin(), costs.end(), mySort);
        int total = 0;
     int n = costs.size()/2;
     for(int i = 0 ; i < n; ++i){
         total += costs[i][0] + costs[i + n][1];
     }
        return total;
    }
private:
    static bool mySort(const vector<int>  & a, const vector<int> & b){
        return (a[0] - a[1] < b[0] - b [1]);
    }
};
 ```
17. stringstream 空格分割字符串：https://blog.csdn.net/oNever_say_love/article/details/49123935

```
#include<iostream>
#include<string>
#include<sstream>
#include<vector>
using namespace std;

int main(){
    //用于存放分割后的字符串 
    vector<string> res;
    //待分割的字符串，含有很多空格 
    string word="   Hello, I want   to learn C++!   ";
    //暂存从word中读取的字符串 
    string result;
    //将字符串读到input中 
    stringstream input(word);
    //依次输出到result中，并存入res中 
    while(input>>result)
        res.push_back(result);
    //输出res 
    for(int i=0;i<res.size();i++){
        cout<<res[i]<<endl;
    }
    return 0;
}
```
```
We can insert text into a stringstream with << and then extract it back with >>
```

与上方不同的：
 ```
     重载输入运算符>>
     重载输出运算符<<
     本节要达到的目标是让复数的输入输出和 int、float 等基本类型一样简单。假设 num1、num2 是复数，那么输出形式就是：
     cout<<num1<<num2<<endl;
     输入形式就是：
     cin>>num1>>num2;
```
