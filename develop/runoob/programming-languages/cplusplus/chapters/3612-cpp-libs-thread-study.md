# C++：C++ 多线程库 <thread>

- 来源：[C++ <thread>](https://www.runoob.com/cplusplus/cpp-libs-thread.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：学习笔记
- 章节序号：3612

## 本章内容

C++11 引入了多线程支持，通过 <thread> 库，开发者可以轻松地在程序中实现并行处理。

本文将将介绍 <thread> 库的基本概念、定义、语法以及如何使用它来创建和管理线程。

线程是程序执行的最小单元，是操作系统能够进行运算调度的最小单位。

在多线程程序中，多个线程可以并行执行，提高程序的执行效率。


### C++ <thread> 库概述

<thread> 库是 C++ 标准库的一部分，提供了创建和管理线程的基本功能，它包括以下几个关键组件：

- std::thread：表示一个线程，可以创建、启动、等待和销毁线程。
- std::this_thread：提供了一些静态成员函数，用于操作当前线程。
- std::thread::id：线程的唯一标识符。


### 创建线程

要创建一个线程，你需要实例化 std::thread 类，并传递一个可调用对象（函数、lambda 表达式或对象的成员函数）作为参数。


## 实例


### 启动线程

创建 std::thread 对象后，线程会立即开始执行，你可以调用 join() 方法来等待线程完成。

```text
t1.join();
t2.join();
```


### 等待线程完成

join() 方法会阻塞当前线程，直到被调用的线程完成执行。


### 销毁线程

当线程执行完毕后，你可以使用 detach() 方法来分离线程，或者让 std::thread 对象超出作用域自动销毁。

```text
t1.detach(); // 线程将继续运行，但无法再被 join 或 detach
```


## 实例：使用 <thread> 创建并行计算

下面是一个使用 <thread> 库实现的并行计算实例，计算两个数的和。


## 实例

输出结果为：

```text
Sum: 30
```

以下实例我们将创建两个线程，每个线程都会执行一个简单的函数，该函数打印一个消息并休眠一段时间：


## 实例

输出结果为：

```text
Hello from thread 2
Hello from thread 1
Main thread finished.
```


### 注意事项

- 线程安全：在多线程环境中，共享资源需要同步访问，以避免数据竞争。
- 线程生命周期：确保在线程执行完毕后正确地处理线程对象，避免资源泄露。


## 类和函数

<thread> 库包含了一系列的类和函数，用于创建、管理和同步线程。

以下是对 C++ <thread> 库的详细介绍:


### 主要组件

- std::thread
- std::mutex
- std::lock_guard
- std::unique_lock
- std::condition_variable
- std::future 和 std::promise
- std::async


### std::thread

std::thread 类用于创建和管理线程。


## 实例

重要方法

- join(): 等待线程结束。
- detach(): 将线程置于后台运行，不再等待线程结束。
- joinable(): 检查线程是否可被 join 或 detach。


### std::mutex

std::mutex 类用于同步对共享资源的访问。


## 实例


### std::lock_guard

std::lock_guard 是一个 RAII 风格的锁管理器，用于自动管理锁的生命周期。


## 实例


### std::unique_lock

std::unique_lock 提供了比 std::lock_guard 更灵活的锁管理。


## 实例


### std::condition_variable

std::condition_variable 用于线程间的等待和通知。


## 实例


### std::future 和 std::promise

std::future 和 std::promise 用于线程间的结果传递。


## 实例


## 后续章节

- std::async
- 实例

## 复习重点

- 能说明 `C++ <thread>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
