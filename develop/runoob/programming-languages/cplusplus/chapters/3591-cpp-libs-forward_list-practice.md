# C++：C++ 容器 <forward_list>

- 来源：[C++ <forward_list>](https://www.runoob.com/cplusplus/cpp-libs-forward_list.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：练习笔记
- 章节序号：3591

## 本章内容

C++ 标准库中的 <forward_list> 是一种容器，它提供了一种单向链表的数据结构。

与双向链表（std::list）不同，std::forward_list 只支持单向遍历。它适用于需要频繁进行前向遍历和插入、删除操作的场景。以下是对 std::forward_list 的详细说明：

单向链表：

- std::forward_list 是单向链表，只能从前往后遍历，不能反向遍历。
- 由于其单向链表的结构，插入和删除操作在已知位置的情况下非常高效（O(1) 复杂度）。

低内存开销：

- 与 std::list 相比，std::forward_list 只需要一个指向下一个节点的指针，节省了内存。

不支持随机访问：

- 不支持通过索引访问元素，不能使用 operator[] 或 at 方法，只能通过迭代器进行访问。


### 语法

std::forward_list 是 C++ 标准库中的一个模板类，定义在 <forward_list> 头文件中。它使用模板参数 T 来指定存储在列表中的元素类型。

以下是 std::forward_list 的基本语法：

```html
#include <forward_list>

std::forward_list<T> list;
```


### 构造函数

std::forward_list 提供了多种构造函数，包括：

- 默认构造函数：创建一个空的 forward_list。
- 带初始值的构造函数：创建一个包含给定初始值的 forward_list。
- 带范围的构造函数：创建一个包含指定范围内元素的 forward_list。


### 常用成员函数

- void push_front(const T& value)：在列表的前端插入一个元素。
- void pop_front()：移除列表前端的元素。
- iterator before_begin()：返回指向列表前端之前的迭代器。
- iterator begin()：返回指向列表前端的迭代器。
- iterator end()：返回指向列表末尾的迭代器。


## 实例

下面是一个使用 std::forward_list 的简单示例，包括创建列表、添加元素、遍历列表和输出结果。


## 实例

当你运行上述代码时，你将看到以下输出：

```text
30 20 10
```

std::forward_list 是 C++ 标准库中一个非常有用的容器，特别适合于需要在列表前端进行频繁插入和删除操作的场景。虽然它不支持随机访问，但在某些情况下，它的性能优势可以弥补这一不足。希望这篇文章能帮助初学者更好地理解和使用 std::forward_list。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C++ <forward_list>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
