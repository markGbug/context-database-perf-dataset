# Python：Python queue 模块

- 来源：[Python queue 模块](https://www.runoob.com/python3/python-queue.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4159

## 本章内容

在 Python 中，queue 模块提供了一个线程安全的队列实现，用于在多线程编程中安全地传递数据。

队列是一种先进先出（FIFO）的数据结构，queue 模块提供了多种队列类型，包括 Queue、LifoQueue 和 PriorityQueue，以满足不同的需求。


## 队列类型


### 1. Queue

Queue 是 queue 模块中最常用的队列类型，它实现了标准的先进先出（FIFO）队列。以下是 Queue 的基本用法：


## 实例


### 2. LifoQueue

LifoQueue 是一种后进先出（LIFO）的队列，类似于栈。以下是 LifoQueue 的基本用法：


## 实例


### 3. PriorityQueue

PriorityQueue 是一种优先级队列，元素按照优先级顺序被取出。以下是 PriorityQueue 的基本用法：


## 实例


## 常用方法


### 1. put(item, block=True, timeout=None)

将 item 放入队列。如果 block 为 True 且队列已满，则等待 timeout 秒，直到队列有空闲空间。如果 timeout 为 None，则无限等待。


### 2. get(block=True, timeout=None)

从队列中获取并移除一个元素。如果 block 为 True 且队列为空，则等待 timeout 秒，直到队列中有元素。如果 timeout 为 None，则无限等待。


### 3. qsize()

返回队列中的元素数量。


### 4. empty()

如果队列为空，返回 True，否则返回 False。


### 5. full()

如果队列已满，返回 True，否则返回 False。


## 线程安全

queue 模块的所有队列类型都是线程安全的，这意味着多个线程可以安全地同时操作同一个队列，而不需要额外的同步机制。这使得 queue 模块成为多线程编程中传递数据的理想选择。


## 示例：多线程队列

以下是一个使用 Queue 在多线程之间传递数据的示例：


## 实例


## 常用的属性和方法

以下是 Python queue 模块（线程安全队列）的常用类、方法及属性的表格说明，包含功能描述和示例：


### queue 模块核心类


### 通用方法（所有队列类都支持）


### 阻塞控制参数


### PriorityQueue 专用用法

元素格式：(priority, data)，优先级越小越先出队


## 实例


### 实例

生产者-消费者模型：


## 实例

优先级任务处理：


## 后续章节

- 实例
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python queue 模块` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
