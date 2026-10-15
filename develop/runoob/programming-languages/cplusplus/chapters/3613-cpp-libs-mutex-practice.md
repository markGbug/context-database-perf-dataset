# C++：C++ 标准库 <mutex>

- 来源：[C++ <mutex>](https://www.runoob.com/cplusplus/cpp-libs-mutex.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：练习笔记
- 章节序号：3613

## 本章内容

在多线程编程中，确保数据的一致性和线程安全是至关重要的。

C++ 标准库提供了一套丰富的同步原语，用于控制对共享资源的访问。

C++ 标准库中的 <mutex> 头文件提供了一组工具，用于在多线程程序中实现线程间的同步和互斥。

<mutex> 头文件是 C++11 引入的，它包含了用于互斥锁（mutex）的类和函数。互斥锁是一种同步机制，用于防止多个线程同时访问共享资源。

互斥锁（Mutex）是一个用于控制对共享资源访问的同步原语。当一个线程需要访问共享资源时，它会尝试锁定互斥锁。如果互斥锁已经被其他线程锁定，请求线程将被阻塞，直到互斥锁被释放。


## 基本语法

在 C++ 中，<mutex> 头文件提供了以下主要类：

- std::mutex：基本的互斥锁。
- std::recursive_mutex：递归互斥锁，允许同一个线程多次锁定。
- std::timed_mutex：具有超时功能的互斥锁。
- std::recursive_timed_mutex：具有超时功能的递归互斥锁。


## 实例


### 1. 使用 std::mutex

下面是一个简单的示例，展示了如何在 C++ 中使用 std::mutex 来同步对共享资源的访问。


## 实例

输出结果：

```text
Final value of shared_resource: 20000
```


### 2. 使用 std::recursive_mutex

递归互斥锁允许同一个线程多次锁定同一个互斥锁。下面是一个使用 std::recursive_mutex 的示例。


## 实例

输出结果：

```text
Incremented shared_resource to 1 (count = 3)
Incremented shared_resource to 2 (count = 2)
Incremented shared_resource to 3 (count = 1)
Incremented shared_resource to 4 (count = 0)
Incremented shared_resource to 5 (count = 3)
Incremented shared_resource to 6 (count = 2)
Incremented shared_resource to 7 (count = 1)
Incremented shared_resource to 8 (count = 0)
Final value of shared_resource: 8
```

代码解析：

- 创建 std::recursive_mutex 对象：std::recursive_mutex rmtx; 是一个递归互斥量，允许同一线程多次获得锁。
- 共享资源：int shared_resource = 0; 是多个线程共同访问的资源。
- 递归函数 recursive_increment：使用 std::lock_guard<std::recursive_mutex> 对 rmtx 上锁。由于使用的是递归互斥量，同一个线程可以多次获得锁。通过 ++shared_resource 增加共享资源的值。函数自身递归调用，演示了递归函数在多次锁定的情况下如何安全地工作。
- 创建和运行线程：std::thread t1(recursive_increment, 3); 和 std::thread t2(recursive_increment, 3); 分别创建两个线程，它们都会执行 recursive_increment(3)。t1.join() 和 t2.join() 等待两个线程执行完毕。


## 注意事项

- 确保在每次锁定互斥锁后，都进行解锁操作，以避免死锁。
- 使用 std::lock_guard 或 std::unique_lock 可以自动管理互斥锁的锁定和解锁，减少出错的可能性。
- 避免在持有互斥锁的情况下调用可能抛出异常的函数，因为这可能导致死锁。

<mutex> 是 C++ 标准库中一个非常重要的头文件，它为多线程编程提供了基本的同步机制。通过使用互斥锁，我们可以确保对共享资源的访问是安全的，从而避免数据竞争和不一致的问题。


## 更多说明


### 1. std::mutex

提供基本的互斥量，确保在同一时刻只有一个线程可以访问共享资源。


## 实例


### 2. std::recursive_mutex

允许同一线程多次获得锁，而不会造成死锁，这对递归函数特别有用。


## 实例


### 3. std::timed_mutex

提供定时的互斥量，可以在尝试获得锁时设置超时时间。


## 实例


### 4. std::recursive_timed_mutex

继承自 std::timed_mutex，允许同一线程多次获得锁，同时支持定时功能。


## 实例


### 5. std::lock_guard

一种自动管理 std::mutex 锁的封装器，使用 RAII 风格，确保在作用域结束时自动释放锁。


## 实例


### 6. std::unique_lock

提供比 std::lock_guard 更灵活的锁管理，可以手动释放和重新获得锁，还支持定时锁定。


## 实例


### 7. std::adopt_lock_t

标志类型，用于指定 std::unique_lock 采用已有的锁。


## 实例


### 8. std::defer_lock_t

功能：标志类型，用于延迟锁定，初始化时不锁定。


## 实例


## 后续章节

- 9. std::try_to_lock_t
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C++ <mutex>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
