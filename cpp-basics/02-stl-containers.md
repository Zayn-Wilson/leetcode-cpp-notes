# STL 容器详解

## 1. vector（动态数组）

```cpp
#include <vector>

// 创建
vector<int> v;                    // 空数组
vector<int> v(n);                 // n个元素，默认值0
vector<int> v(n, val);            // n个元素，初始值val
vector<int> v = {1, 2, 3};        // 初始化列表

// 常用操作
v.push_back(x);      // 尾部添加元素 O(1)
v.pop_back();        // 删除尾部元素 O(1)
v.size();            // 元素个数
v.empty();           // 是否为空
v.clear();           // 清空
v.front();           // 第一个元素
v.back();            // 最后一个元素
v[i];                // 访问第i个元素
v.resize(n);         // 调整大小

// 遍历
for (int i = 0; i < v.size(); i++) { }
for (int x : v) { }
for (auto it = v.begin(); it != v.end(); it++) { }
```

## 2. string（字符串）

```cpp
#include <string>

// 创建
string s;
string s = "hello";
string s(n, 'a');    // n个字符'a'

// 常用操作
s.length();          // 长度（同 s.size()）
s.empty();           // 是否为空
s += "world";        // 拼接
s.substr(pos, len);  // 子串
s.find("lo");        // 查找，返回位置或string::npos
s.push_back('!');    // 添加字符
s.pop_back();        // 删除最后一个字符
s[i];                // 访问第i个字符

// 字符操作
isalpha(c);          // 是否是字母
isdigit(c);          // 是否是数字
isalnum(c);          // 是否是字母或数字
tolower(c);          // 转小写
toupper(c);          // 转大写
```

## 3. unordered_map（哈希表）

```cpp
#include <unordered_map>

// 创建
unordered_map<string, int> mp;

// 常用操作
mp["key"] = value;           // 插入/修改
mp.count("key");             // 是否存在（0或1）
mp.find("key");              // 查找，返回迭代器
mp.erase("key");             // 删除
mp.size();                   // 元素个数
mp.clear();                  // 清空

// 遍历
for (auto& [key, value] : mp) {
    cout << key << ": " << value << endl;
}

// 或者
for (auto& p : mp) {
    cout << p.first << ": " << p.second << endl;
}
```

## 4. unordered_set（哈希集合）

```cpp
#include <unordered_set>

// 创建
unordered_set<int> st;
unordered_set<int> st = {1, 2, 3};

// 常用操作
st.insert(x);        // 插入
st.count(x);         // 是否存在（0或1）
st.erase(x);         // 删除
st.size();           // 元素个数
st.clear();          // 清空

// 遍历
for (int x : st) {
    cout << x << endl;
}
```

## 5. map / set（有序容器）

```cpp
#include <map>
#include <set>

// 有序，基于红黑树，操作 O(log n)
map<string, int> mp;     // 按key排序
set<int> st;             // 元素有序

// 操作与 unordered 版本类似
// 额外支持：
st.lower_bound(x);   // >= x 的第一个元素
st.upper_bound(x);   // > x 的第一个元素
```

## 6. queue（队列）

```cpp
#include <queue>

queue<int> q;

q.push(x);           // 入队
q.pop();             // 出队（不返回值）
q.front();           // 队首元素
q.back();            // 队尾元素
q.empty();           // 是否为空
q.size();            // 元素个数
```

## 7. stack（栈）

```cpp
#include <stack>

stack<int> stk;

stk.push(x);         // 入栈
stk.pop();           // 出栈（不返回值）
stk.top();           // 栈顶元素
stk.empty();         // 是否为空
stk.size();          // 元素个数
```

## 8. priority_queue（优先队列/堆）

```cpp
#include <queue>

// 大顶堆（默认）
priority_queue<int> pq;

// 小顶堆
priority_queue<int, vector<int>, greater<int>> minPq;

pq.push(x);          // 插入
pq.pop();            // 删除堆顶
pq.top();            // 堆顶元素
pq.empty();          // 是否为空
pq.size();           // 元素个数

// 自定义比较
auto cmp = [](pair<int,int>& a, pair<int,int>& b) {
    return a.first > b.first;  // 小顶堆
};
priority_queue<pair<int,int>, vector<pair<int,int>>, decltype(cmp)> pq(cmp);
```

## 9. deque（双端队列）

```cpp
#include <deque>

deque<int> dq;

dq.push_front(x);    // 头部插入
dq.push_back(x);     // 尾部插入
dq.pop_front();      // 头部删除
dq.pop_back();       // 尾部删除
dq.front();          // 头部元素
dq.back();           // 尾部元素
dq[i];               // 随机访问
```

## 10. pair（键值对）

```cpp
#include <utility>

pair<int, string> p = {1, "hello"};
pair<int, string> p = make_pair(1, "hello");

p.first;             // 第一个元素
p.second;            // 第二个元素

// 常用于返回两个值
pair<int, int> findMinMax(vector<int>& nums) {
    return {*min_element(nums.begin(), nums.end()),
            *max_element(nums.begin(), nums.end())};
}
```