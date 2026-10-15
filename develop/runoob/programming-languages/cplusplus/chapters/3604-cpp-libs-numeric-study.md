# C++：C++ 标准库 <numeric>

- 来源：[C++ <numeric>](https://www.runoob.com/cplusplus/cpp-libs-numeric.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：学习笔记
- 章节序号：3604

## 本章内容

在日常 C++ 开发中，我们经常会遇到如下需求：

- 求数组总和 / 连乘
- 计算前缀和用于区间查询
- 批量累积生成新序列
- 做向量之间的内积（点积）

如果你还在手写 for 循环，那么 <numeric> 正是你应该掌握的标准库工具。

C++ 标准库中的 <numeric> 头文件提供了一组用于数值计算的函数模板，这些函数可以对容器中的元素进行各种数值操作，如求和、乘积、最小值、最大值等。这些函数模板非常强大，可以应用于任何类型的容器，包括数组、向量、列表等。

在使用 <numeric> 头文件中的函数之前，需要在你的 C++ 程序中包含这个头文件：

```html
#include <numeric>
```


## 常用函数

- <numeric> 是 C++ 处理数值序列计算的核心头文件，专注于归约、累积、差分等操作，兼容所有STL容器；
- 基础函数（accumulate/partial_sum/iota）是C++98/11的核心，满足绝大多数常规数值计算需求；
- C++17 新增的 reduce/inclusive_scan 等并行函数，可显著提升大数据量下的计算效率，需配合并行执行策略使用。


### 1. accumulate

accumulate 函数用于计算容器中所有元素的总和。它接受三个参数：容器的开始迭代器、结束迭代器和初始值。

语法:

```html
template <InputIterator Iter, class T>
T accumulate(Iter first, Iter last, T init);
```

实例:


## 实例


### 2. inner_product

inner_product 函数用于计算两个容器中对应元素乘积的总和。

语法:

```html
template <InputIterator1 Iter1, InputIterator2 Iter2, class T>
T inner_product(Iter1 first1, Iter1 last1, Iter2 first2, T init);
```

实例:


## 实例


### 3. partial_sum

partial_sum 函数用于计算容器中元素的部分和，并将结果存储在另一个容器中。

语法:

```html
template <InputIterator InIter, OutputIterator OutIter>
OutIter partial_sum(InIter first, InIter last, OutIter result);
```

实例:


## 实例


### 4. adjacent_difference

adjacent_difference 函数用于计算容器中相邻元素的差值，并将结果存储在另一个容器中。

语法:

```html
template <InputIterator InIter, OutputIterator OutIter>
OutIter adjacent_difference(InIter first, InIter last, OutIter result);
```

实例:


## 实例


### 5. std::gcd

使用 std::gcd 计算两个整数的最大公约数：


## 实例


### 6. std::lcm

使用 std::lcm 计算两个整数的最小公倍数：


## 实例


### 7. std::iota


## 实例

使用 std::iota 填充范围内的序列值。

```html
template<class ForwardIt, class T>
void iota(ForwardIt first, ForwardIt last, T value);
```


### 8.查找最大值与最小值

min_element 和 max_element 函数用于找到容器中的最大值和最小值。


## 实例

输出结果为：

```text
Min: 1
Max: 9
Sum: 23
Average: 3.83333
```


## 复习重点

- 能说明 `C++ <numeric>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
