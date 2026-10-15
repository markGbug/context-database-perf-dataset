# C++：C++ 容器类 <priority_queue>

- 来源：[C++ <priority_queue>](https://www.runoob.com/cplusplus/cpp-libs-priority_queue.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：练习笔记
- 章节序号：3595

## 本章内容

在 C++ 中，<priority_queue> 是标准模板库（STL）的一部分，用于实现优先队列。

优先队列是一种特殊的队列，它允许我们快速访问队列中具有最高（或最低）优先级的元素。

在 C++ 中，priority_queue 默认是一个最大堆，这意味着队列的顶部元素总是具有最大的值。

priority_queue 是一个容器适配器，它提供了对底层容器的堆操作。它不提供迭代器，也不支持随机访问。


### 语法

以下是 priority_queue 的基本语法：

```java
#include <queue>

// 声明一个整型优先队列
priority_queue<int> pq;

// 声明一个自定义类型的优先队列，需要提供比较函数
struct compare {
    bool operator()(int a, int b) {
        return a > b; // 这里定义了最小堆
    }
};
priority_queue<int, vector<int>, compare> pq_min;
```


### 常用操作

- empty(): 检查队列是否为空。
- size(): 返回队列中的元素数量。
- top(): 返回队列顶部的元素（不删除它）。
- push(): 向队列添加一个元素。
- pop(): 移除队列顶部的元素。


## 实例

下面是一个使用 priority_queue 的简单实例，我们将创建一个最大堆，并展示如何添加元素和获取队列顶部的元素。


## 实例

输出结果：

```text
队列中的元素：
50
30
20
10
```


## 自定义优先级

如果你需要一个最小堆，可以通过自定义比较函数来实现：


## 实例

输出结果：

```text
最小堆中的元素：
10
20
30
50
```

<priority_queue> 是C++ STL中一个非常有用的容器，特别适合需要快速访问最高或最低优先级元素的场景。通过自定义比较函数，我们可以轻松地实现最大堆或最小堆。希望这篇文章能帮助初学者更好地理解和使用 priority_queue。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C++ <priority_queue>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
