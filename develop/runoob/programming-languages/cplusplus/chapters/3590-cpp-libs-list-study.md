# C++：C++ 容器类 <list>

- 来源：[C++ <list>](https://www.runoob.com/cplusplus/cpp-libs-list.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：学习笔记
- 章节序号：3590

## 本章内容

C++ 标准库提供了丰富的功能，其中 <list> 是一个非常重要的容器类，用于存储元素集合，支持双向迭代器。

<list> 是 C++ 标准模板库（STL）中的一个序列容器，它允许在容器的任意位置快速插入和删除元素。与数组或向量（<vector>）不同，<list> 不需要在创建时指定大小，并且可以在任何位置添加或删除元素，而不需要重新分配内存。


### 语法

以下是 <list> 容器的一些基本操作：

- 包含头文件：#include <list>
- 声明列表：std::list<T> mylist;，其中 T 是存储在列表中的元素类型。
- 插入元素：mylist.push_back(value);
- 删除元素：mylist.pop_back(); 或 mylist.erase(iterator);
- 访问元素：mylist.front(); 和 mylist.back();
- 遍历列表：使用迭代器 for (auto it = mylist.begin(); it != mylist.end(); ++it)


### 特点

- 双向迭代：<list> 提供了双向迭代器，可以向前和向后遍历元素。
- 动态大小：与数组不同，<list> 的大小可以动态变化，不需要预先分配固定大小的内存。
- 快速插入和删除：可以在列表的任何位置快速插入或删除元素，而不需要像向量那样移动大量元素。


### 声明与初始化

<list> 的声明和初始化与其他容器类似：

```java
#include <iostream>
#include <list>

int main() {
    std::list<int> lst1;                  // 空的list
    std::list<int> lst2(5);               // 包含5个默认初始化元素的list
    std::list<int> lst3(5, 10);           // 包含5个元素，每个元素为10
    std::list<int> lst4 = {1, 2, 3, 4};   // 使用初始化列表

    return 0;
}
```


## 实例

下面是一个使用 <list> 的简单示例，包括创建列表、添加元素、遍历列表和输出结果。


## 实例

输出结果:

```text
First element: 10
Last element: 30
List elements: 10 20 30
List elements after removing the last element: 10 20
```


## 常用成员函数

以下是 <list> 中一些常用的成员函数：


### 实例

1、基本操作


## 实例

2、插入和删除特定位置的元素


## 实例

3、排序和去重


## 实例

4、合并和反转


## 实例


## 与其他容器对比


## 注意事项

- <list> 的元素是按插入顺序存储的，而不是按元素值排序。
- 由于 <list> 的元素存储在不同的内存位置，所以它不适合需要随机访问的场景。
- 与向量相比，<list> 的内存使用效率较低，因为每个元素都需要额外的空间来存储指向前后元素的指针。

通过这个简单的介绍和示例，初学者应该能够对 C++ 的 <list> 容器有一个基本的了解，并能够开始使用它来解决实际问题。


## 复习重点

- 能说明 `C++ <list>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
