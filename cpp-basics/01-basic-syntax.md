# C++ 基本语法复习

## 1. 数据类型

```cpp
// 整数类型
int a = 10;           // 32位整数
long long b = 1e18;   // 64位整数（LeetCode常用）

// 浮点类型
double c = 3.14;

// 字符和字符串
char ch = 'a';
string s = "hello";

// 布尔类型
bool flag = true;
```

## 2. 输入输出

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;           // 输入
    cout << n << endl;  // 输出
    return 0;
}
```

## 3. 数组

```cpp
// 静态数组
int arr[100];
int arr2[3] = {1, 2, 3};

// 动态数组（推荐）
vector<int> vec;
vector<int> vec2(n, 0);      // n个元素，初始值为0
vector<int> vec3 = {1, 2, 3};

// 二维数组
vector<vector<int>> matrix(m, vector<int>(n, 0));
```

## 4. 条件语句

```cpp
if (condition) {
    // ...
} else if (condition2) {
    // ...
} else {
    // ...
}

// 三元运算符
int result = (a > b) ? a : b;
```

## 5. 循环

```cpp
// for 循环
for (int i = 0; i < n; i++) {
    // ...
}

// 范围 for 循环（C++11）
for (int x : vec) {
    cout << x << endl;
}

// 引用遍历（可修改元素）
for (int& x : vec) {
    x *= 2;
}

// while 循环
while (condition) {
    // ...
}
```

## 6. 函数

```cpp
// 基本函数
int add(int a, int b) {
    return a + b;
}

// 引用传参（避免拷贝）
void modify(vector<int>& vec) {
    vec[0] = 100;
}

// Lambda 表达式（C++11）
auto cmp = [](int a, int b) {
    return a > b;
};
sort(vec.begin(), vec.end(), cmp);
```

## 7. 常用头文件

```cpp
#include <iostream>     // 输入输出
#include <vector>       // 动态数组
#include <string>       // 字符串
#include <algorithm>    // 算法（sort, max, min等）
#include <unordered_map>// 哈希表
#include <unordered_set>// 哈希集合
#include <queue>        // 队列、优先队列
#include <stack>        // 栈
#include <cmath>        // 数学函数
#include <climits>      // INT_MAX, INT_MIN等

using namespace std;
```

## 8. 常用技巧

```cpp
// 交换两个变量
swap(a, b);

// 取最大最小值
int maxVal = max(a, b);
int minVal = min(a, b);
int maxOfThree = max({a, b, c});

// 绝对值
int absVal = abs(x);

// 整数边界
int maxInt = INT_MAX;   // 2147483647
int minInt = INT_MIN;   // -2147483648
long long maxLL = LLONG_MAX;

// 字符串转数字
int num = stoi("123");
long long num2 = stoll("123456789");

// 数字转字符串
string s = to_string(123);
```