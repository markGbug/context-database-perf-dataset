# C++：C++ 标准库 <future>

- 来源：[C++ <future>](https://www.runoob.com/cplusplus/cpp-libs-future.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：练习笔记
- 章节序号：3615

## 本章内容

C++11 引入了 <future> 头文件，它提供了一种异步编程的机制，允许程序在等待某个操作完成时继续执行其他任务。<future> 库是 C++ 标准库中并发编程的一部分，它允许程序员以一种更简洁和安全的方式处理异步操作。

<future> 库中定义了几个关键的类型：

- std::future：表示异步操作的结果，可以查询操作的状态，获取结果或等待操作完成。
- std::promise：用于与 std::future 配对，用于设置异步操作的结果。
- std::packaged_task：封装一个函数或可调用对象，使其可以作为异步任务执行。


### std::promise

std::promise 用于设置异步操作的结果。它与 std::future 配对使用。


## 实例

输出结果：

```text
Future value: 10
```


### std::packaged_task

std::packaged_task 封装一个函数或可调用对象，使其可以作为异步任务执行。


## 实例

输出结果：

```text
Result: 3
```


### std::async

std::async 是一个方便的函数，用于启动异步任务。它可以立即返回一个 std::future 对象。


## 实例

输出结果：

```text
Result: 25
```


## 异常处理

当异步操作抛出异常时，std::future 会捕获这个异常，并且可以通过调用 .get() 方法来重新抛出它。


## 实例

输出结果：

```text
Caught exception: Exception thrown
```

<future> 库为 C++ 程序员提供了一种简单而强大的异步编程方式。通过使用 std::promise、std::packaged_task 和 std::async，我们可以轻松地在 C++ 程序中实现并发和异步操作。同时，异常处理机制也确保了程序的健壮性。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C++ <future>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
