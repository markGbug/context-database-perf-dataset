# C++：C++ 标准库 <condition_variable>

- 来源：[C++ <condition_variable>](https://www.runoob.com/cplusplus/cpp-libs-condition_variable.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：学习笔记
- 章节序号：3614

## 本章内容

在多线程编程中，线程间的同步是一个非常重要的问题。

C++11 标准引入了 <condition_variable> 头文件，它提供了一种机制，允许线程在某些条件不满足时挂起，直到其他线程通知它们条件已经满足。

condition_variable是用于线程间同步的一种高级工具，它比使用低级同步原语（如互斥锁和条件变量）更加安全和方便。

condition_variable是一个类模板，用于在多线程环境中实现线程间的同步。它允许一个或多个线程等待某个条件变为真，而其他线程可以唤醒这些等待的线程。


## 语法

以下是condition_variable的基本语法：

```java
#include <condition_variable>

void notify_one() {
    // 唤醒一个等待的线程
}

void notify_all() {
    // 唤醒所有等待的线程
}

template <class Mutex>
class condition_variable {
public:
    condition_variable();
    ~condition_variable();

    void wait(unique_lock<mutex>& lock);
    void wait_for(unique_lock<mutex>& lock, chrono::duration<Rep, Period> const& rel_time);
    void wait_until(unique_lock<mutex>& lock, chrono::time_point<Clock, Duration> const& abs_time);

    void notify_one() noexcept;
    void notify_all() noexcept;
};
```


## 实例

下面是一个使用condition_variable的简单示例，展示了生产者-消费者问题的基本实现。


## 实例

这个程序的输出可能会有所不同，因为它依赖于线程调度。但是，你会看到生产者生产产品，然后消费者消费这些产品。输出将类似于：

```text
Producer 1 produced 100
Producer 2 produced 200
Consumer 1 consumed 100
Producer 1 produced 101
Consumer 2 consumed 200
Producer 2 produced 201
Consumer 1 consumed 101
...
```


## 注意事项

- 使用condition_variable时，必须确保在等待之前获取互斥锁，并且在唤醒后释放互斥锁。
- wait、wait_for和wait_until函数都会释放互斥锁，然后在等待期间重新获取它。
- notify_one唤醒一个等待的线程，而notify_all唤醒所有等待的线程。


## 复习重点

- 能说明 `C++ <condition_variable>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
