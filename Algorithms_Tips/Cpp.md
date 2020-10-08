# Cpp
#### https://www.cnblogs.com/lsgxeva/p/7787438.html c++11 类默认函数的控制："=default" 和 "=delete"函数
#### https://www.cnblogs.com/sunchaothu/p/10389842.html c++单例模式

#### https://www.cnblogs.com/1024th/p/10623541.html 排列组合公式
```
 tgamma(n) == (n-1)!
```
#### HOW TO SPLIT A STRING IN C++ http://www.martinbroadhurst.com/how-to-split-a-string-in-c.html
#### string和stringstream用法总结 https://blog.csdn.net/zaishaoyi/article/details/46682033
#### C++:cin、cin.getline()、getline()的用法 https://blog.csdn.net/u011630575/article/details/79721024
#### C++ 标准输出控制小数点后位数的方法 https://blog.csdn.net/JIEJINQUANIL/article/details/51394167
#### unordered_map 和 unordered_set 都是不按值排序的，而map和set会自动按key或set中的值从小到大排序
#### STL比较好的总结：https://www.cnblogs.com/skyfsm/p/6934246.html
#### 刷题模板总结： https://blog.csdn.net/fuxuemingzhu/article/details/101900729
```
是的话返回>0的int
不是的话返回0
 if (isdigit(cur))
isalpha(cur)
```
```
最近发现一个在C++中引用很广泛的一个头文件

#include <bits/stdc++.h>

了解发现它是C++中支持的一个几乎万能的头文件，几乎包含所有的可用到的C++库函数。以后写代码就可以直接引用这一个头文件了，不需要在写一大堆vector、string、map、stack、、、、。

https://blog.csdn.net/snow_rain_1314/article/details/80014301
```
#### String char int 转换
```
string getString(char x) 
{ 
    // string class has a constructor 
    // that allows us to specify size of 
    // string as first parameter and character 
    // to be filled in given size as second 
    // parameter. 
    string s(1, x); 
  
    return s;    
} 
  
int main() { 
  cout << getString('a'); 
  return 0; 
} 
```
```
stringstream 用于类型转换更方便 #include<sstream>
```
```
int to string
string std::to_string (int val);

string to int
int myint1 = std::stoi(str1);
int myint2 = std::stoi(str2);

```

```
string to char*
const char* c_str() const noexcept;

  char * cstr = new char [str.length()+1];
  std::strcpy (cstr, str.c_str());
```
```
std::reverse(a.begin(),a.end()), #include<algorithm>
```
#### 判断容器是否为空： .empty()

#### 记得用 size_t 类型，记得用long

#### struct默认public，class默认private

#### 函数返回值的几种情况https://blog.csdn.net/hankai1024/article/details/8039770
#### 1. ```unordered_map``` 直接map[key] = value即可， 而vector等如果相应元素没初始化，需要用push_back()，同时unordered_map<int,int> value默认初始值为0;
#### 2. ```stringstream fstream iostream``` 是io都可以用的
#### 3. 数据结构中各种树总结https://www.jianshu.com/p/6f573afd2501
#### 4. 自平衡二叉树旋转方法总结https://blog.csdn.net/saasanken/article/details/80796178
#### 5. 红黑树旋转方法总结：维基百科  https://zh.wikipedia.org/wiki/%E7%BA%A2%E9%BB%91%E6%A0%91
#### 6. 各种排序算法及比较https://blog.csdn.net/yushiyi6453/article/details/76407640
#### 7. 任何```container``` 都可以用 ```.size()``` 得到长度, 用reverse(a.begin(), a.end())进行reverse
#### 8. ```sliding window``` (leetcode 438 Find All Anagrams in a String 经典基础)
#### 9. ```vector``` 重载了 ==，比较相等的时候可以直接用```vector``` 重载了 =， 可以用于深拷贝
#### 10. 数据结构
In container, 
```
front() back() return a reference to the element, begin(), end() return iterator, 
 pop() Removes the element on top, top() Returns a reference to the top element
 ```

   ##### (1)vector:
```
push_back(), void pop_back(), begin(), end(), front(), back(), myvector.resize(12)(初始化的时候用);

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
///注意此处stack和queue不同 top();/// push(); void pop();
```
   ##### (4)queue:
```
///注意此处stack和queue不同 front(); back();/// push(); void pop();
```
   ##### (5)unordered_map: 
```
begin(); end(); 

count(): 
Searches the container for elements whose key is k and returns the number of elements found. 
Because unordered_map containers do not allow for duplicate keys, this means that the function actually
returns 1 if an element with that key exists in the container, and zero otherwise.
```
```
遍历map
You can achieve this like following :

map<string, int>::iterator it;
for ( it = symbolTable.begin(); it != symbolTable.end(); it++ )
{
    std::cout << it->first  // string (key)
              << ':'
              << it->second   // string's value 
              << std::endl ;
}

With C++11 ( and onwards ),
for (auto const& x : symbolTable)
{
    std::cout << x.first  // string (key)
              << ':' 
              << x.second // string's value 
              << std::endl ;
}

```
##### (6)deque:
```

push_back
Add element at the end (public member function )
push_front
Insert element at beginning (public member function )
pop_back
Delete last element (public member function )
pop_front
Delete first element (public member function )
```
##### (7)list:
```
push_front
Insert element at beginning (public member function )
pop_front
Delete first element (public member function )
emplace_back 
Construct and insert element at the end (public member function )
push_back
Add element at the end (public member function )
pop_back
Delete last element (public member function )
emplace 
Construct and insert element (public member function )
insert
Insert elements (public member function )
```

##### (8) set
```
size_type count (const value_type& val) const;
Count elements with a specific value
Searches the container for elements equivalent to val and returns the number of matches.

Because all elements in a set container are unique, the function can only return 1 (if the element is found) or zero (otherwise).
```

```
//insert之后的内容是排序的
// set::insert (C++98)
#include <iostream>
#include <set>

int main ()
{
  std::set<int> myset;
  std::set<int>::iterator it;
  std::pair<std::set<int>::iterator,bool> ret;

  // set some initial values:
  for (int i=1; i<=5; ++i) myset.insert(i*10);    // set: 10 20 30 40 50

  ret = myset.insert(20);               // no new element inserted

  if (ret.second==false) it=ret.first;  // "it" now points to element 20

  myset.insert (it,25);                 // max efficiency inserting
  myset.insert (it,24);                 // max efficiency inserting
  myset.insert (it,26);                 // no max efficiency inserting

  int myints[]= {5,10,15};              // 10 already in set, not inserted
  myset.insert (myints,myints+3);

  std::cout << "myset contains:";
  for (it=myset.begin(); it!=myset.end(); ++it)
    std::cout << ' ' << *it;
  std::cout << '\n';

  return 0;
}
```
##### (9) priority_queue
```
push() pop() top() size()
// constructing priority queues
#include <iostream>       // std::cout
#include <queue>          // std::priority_queue
#include <vector>         // std::vector
#include <functional>     // std::greater

class mycomparison
{
  bool reverse;
public:
  mycomparison(const bool& revparam=false)
    {reverse=revparam;}
  bool operator() (const int& lhs, const int&rhs) const
  {
    if (reverse) return (lhs>rhs);
    else return (lhs<rhs);
  }
};

int main ()
{
  int myints[]= {10,60,50,20};

  std::priority_queue<int> first;
  std::priority_queue<int> second (myints,myints+4);
  std::priority_queue<int, std::vector<int>, std::greater<int> >
                            third (myints,myints+4);
  // using mycomparison:
  typedef std::priority_queue<int,std::vector<int>,mycomparison> mypq_type;

  mypq_type fourth;                       // less-than comparison
  mypq_type fifth (mycomparison(true));   // greater-than comparison

  return 0;
}

The example does not produce any output, but it constructs different priority_queue objects:
- First is empty.
- Second contains the four ints defined for myints, with 60 (the highest) at its top.
- Third has the same four ints, but because it uses greater instead of the default (which is less), it has 10 as its top element.
- Fourth and fifth are very similar to first: they are both empty, except that these use mycomparison for comparisons, which is a special stateful comparison function that behaves differently depending on a flag set on construction.

```

#### 11. 
```Two pointer```( leetcode 986. Interval List Intersections 经典基础）
#### 12. 数组下标记得用
```
size_t
```
#### 13. 
```
unique_ptr<TrieNode> root;
Trie():root(new TrieNode()) {}
```
此指针指向的东西会自动析构 
#### 14. c++ STL 四种智能指针https://blog.csdn.net/k346k346/article/details/81478223
#### 15. c++ map与unordered_map区别及使用 https://blog.csdn.net/BillCYJ/article/details/78985895 
#### 16. sort:
 利用greater 进行从大到小sort（默认从小到大）
 ```
 #include <iostream>
#include <algorithm>
using namespace std;
int main() {
    int arr[] = { 2, 4, 5, 3, 1 };
    sort(arr, arr + 5, greater<int>());
    for(int i = 0;i < 5;i++){
    	cout<< arr[i] <<" ";
    } 
    return 0;
}

 ```
 自定义sort
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
                                 
 ```
根据两个条件进行sort
 bool mySort(const vector<int>& a, const vector<int>& b){
    if(a[2] == b[2]){
        return a[3] < b[3];
    }
    else{
        return a[2] > b[2];
    }
}

vector<int> getUnallotedUsers(vector<vector<int>> input,int shares){
    vector<int> ans;
    if(shares <= 0){
        for(int i = 0; i < input.size(); ++i){
            ans.push_back(input[i][0]);
        }
        sort(ans.begin(),ans.end());
        return ans;
    }
    sort(input.begin(), input.end(), mySort);
    size_t i = 0;
    for(; i < input.size() - 1; ++i){
        int rest = 0;
        if(input[i][2] == input[i + 1][2]){
        while(input[i][2] == input[i + 1][2] && shares > 0){
            --shares;        
            rest += (input[i][1] - 1);
            ++i;
          }
        if(shares <= 0){
            --i;
            break;
        }
            --shares;
            rest += (input[i][1] - 1);
        if(shares <= 0){
            break;
        }
        if(shares - rest <= 0){
            shares -= rest;
            break;
        }
        }
        else{
            shares -= input[i][1];
            if(shares <= 0){
                break;
            }
        }
        }
    ++i;
    if(i == input.size() - 1){
        if(shares <= 0){
            ans.push_back(input[i][0]);
            return ans;
        }
        else{
            return ans;
        }
    }
    for(int j = i; j < input.size(); ++j){
        ans.push_back(input[j][0]);
    }
    sort(ans.begin(),ans.end());
    return ans;
}

int main() {
    vector<vector<int>> input = {{1,5,5,0},{2,7,8,1},{3,7,5,1},{4,10,3,3}};
    vector<int> output = getUnallotedUsers(input, 18);
        for(int val: output){
             cout << val << endl;
        }
    return EXIT_SUCCESS;
}
 ```
#### 17. stringstream 空格分割字符串：https://blog.csdn.net/oNever_say_love/article/details/49123935

并且可用于类型转换
```
空格分割
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

符号分割
stringstream s1(artifacts);
    string s;
    while (getline(s1, s, ',')) arts.push_back(s);
    s = "";
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
#### 18.Erase–remove idiom

From Wikipedia, the free encyclopedia

The erase–remove idiom cannot be used for containers that return const_iterator (e.g.: set)[5]

The erase–remove idiom is a common C++ technique to eliminate elements that fulfill a certain criterion from a C++ Standard Library container.[1][2][3]
```
// Use g++ -std=c++11 or clang++ -std=c++11 to compile.

#include <algorithm>  // remove and remove_if
#include <iostream>
#include <vector>  // the general-purpose vector container

bool IsOdd(int i) { return i & 1; }

void Print(const std::vector<int>& vec) {
  for (const auto& i : vec) {
    std::cout << i << ' ';
  }
  std::cout << std::endl;
}

int main() {
  // Initializes a vector that holds numbers from 0-9.
  std::vector<int> v = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};
  Print(v);

  // Removes all elements with the value 5.
  v.erase(std::remove(v.begin(), v.end(), 5), v.end());
  Print(v);

  // Removes all odd numbers.
  v.erase(std::remove_if(v.begin(), v.end(), IsOdd), v.end());
  Print(v);
}

/*
Output:
0 1 2 3 4 5 6 7 8 9
0 1 2 3 4 6 7 8 9
0 2 4 6 8
*/
```
