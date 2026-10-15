# C++：C++ 标准库 <deque>

- 来源：[C++ <deque>](https://www.runoob.com/cplusplus/cpp-libs-deque.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：练习笔记
- 章节序号：3592

## 本章内容

在 C++中，<deque> 是标准模板库（STL）的一部分，它提供了双端队列（double-ended queue）的实现。

双端队列是一种允许在两端进行插入和删除操作的线性数据结构。

<deque> 的全称是 "double-ended queue"，它在C++中以模板类的形式存在，允许存储任意类型的数据。

<deque> 是一个动态数组，它提供了快速的随机访问能力，同时允许在两端进行高效的插入和删除操作。这使得 <deque> 成为处理需要频繁插入和删除元素的场景的理想选择。


### 语法

在 C++ 中，使用 <deque> 需要包含头文件 #include <deque>。以下是 <deque> 的基本语法：

```java
#include <iostream>
#include <deque>

int main() {
    std::deque<int> myDeque; // 创建一个整数类型的双端队列
    // 接下来可以进行插入、删除等操作
    return 0;
}
```


## 常用操作

下面是 std::deque 容器的一些常用成员函数：


## 实例

下面是一个使用 <deque> 的简单示例，包括元素的插入、访问和删除操作。


## 实例

输出结果:

```text
Deque contains: 5 10 20
Deque after popping: 10
```

在不知道 deque 长度的时候，可以使用 deque.front() 与 deque.back() 来访问头尾元素：


## 实例

输出结果为：

```text
Front element: 5
Back element: 20
Modified front element: 15
Modified back element: 25
```

注意：在使用 front() 或 back() 之前，确保双端队列不为空，否则会引发未定义的行为。如果需要检查双端队列是否为空，可以使用 empty() 成员函数。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C++ <deque>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
