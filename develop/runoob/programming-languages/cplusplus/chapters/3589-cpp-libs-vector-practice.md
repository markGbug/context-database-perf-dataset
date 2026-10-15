# C++：C++ 容器类 <vector>

- 来源：[C++ <vector>](https://www.runoob.com/cplusplus/cpp-libs-vector.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：练习笔记
- 章节序号：3589

## 本章内容

## 简介

C++ 标准库（Standard Template Library, STL）是 C++ 的一个重要组成部分，它提供了一组通用的模板类和函数，用于处理数据集合。<vector> 是 STL 中的一个容器类，用于存储动态大小的数组。

<vector> 是一个序列容器，它允许用户在容器的末尾快速地添加或删除元素。与数组相比，<vector> 提供了更多的功能，如自动调整大小、随机访问等。


### 语法

在 C++ 中，使用 <vector> 需要包含头文件 <<vector>>。以下是一些基本的语法：

- 声明一个 vector： std::vector<int> myVector;
- 添加元素： myVector.push_back(10);
- 访问元素： int firstElement = myVector[0];
- 获取元素数量： size_t size = myVector.size();
- 清空 vector： myVector.clear();


### 声明与初始化

<vector> 需要指定元素类型，可通过多种方式进行初始化：

```java
#include <iostream>
#include <vector>

int main() {
    std::vector<int> vec1;                  // 空的vector
    std::vector<int> vec2(5);               // 长度为5的vector，元素默认初始化
    std::vector<int> vec3(5, 10);           // 长度为5的vector，元素值为10
    std::vector<int> vec4 = {1, 2, 3, 4};   // 使用初始化列表初始化

    return 0;
}
```


## 实例

下面是一个使用 <vector> 的简单示例，包括输出结果。


## 实例

输出结果:

```text
Vector contains: 10 20 30
After adding more elements, vector contains: 10 20 30 40 50
The first element is: 10
The vector is now empty.
```


## 常用成员函数

以下是 <vector> 中的一些常用成员函数：


### 实例

1、基本操作


## 实例

2、动态增加和删除元素


## 实例

3、边界检查和安全访问


## 实例

4、预分配容量


## 实例


### 与其他容器对比

<vector> 是 C++ STL 中一个非常有用的容器，它提供了动态数组的功能，使得元素的添加和删除变得更加灵活和方便。通过上述示例，初学者可以快速了解 <vector> 的基本用法和操作。随着学习的深入，你将发现 <vector> 在实际编程中的强大功能和广泛应用。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C++ <vector>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
