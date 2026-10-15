# C#：C# 多线程

- 来源：[C# 多线程](https://www.runoob.com/csharp/csharp-multithreading.html)
- 分类：后端开发
- 技术：C#
- 笔记类型：概念卡
- 章节序号：0789

## 本章内容

线程 被定义为程序的执行路径。每个线程都定义了一个独特的控制流。如果您的应用程序涉及到复杂的和耗时的操作，那么设置不同的线程执行路径往往是有益的，每个线程执行特定的工作。

线程是轻量级进程。一个使用线程的常见实例是现代操作系统中并行编程的实现。使用线程节省了 CPU 周期的浪费，同时提高了应用程序的效率。

到目前为止我们编写的程序是一个单线程作为应用程序的运行实例的单一的过程运行的。但是，这样子应用程序同时只能执行一个任务。为了同时执行多个任务，它可以被划分为更小的线程。


## 线程生命周期

线程生命周期开始于 System.Threading.Thread 类的对象被创建时，结束于线程被终止或完成执行时。

下面列出了线程生命周期中的各种状态：

- 未启动状态：当线程实例被创建但 Start 方法未被调用时的状况。
- 就绪状态：当线程准备好运行并等待 CPU 周期时的状况。
- 不可运行状态：下面的几种情况下线程是不可运行的： 已经调用 Sleep 方法 已经调用 Wait 方法 通过 I/O 操作阻塞
- 死亡状态：当线程已完成执行或已中止时的状况。


## 主线程

在 C# 中，System.Threading.Thread 类用于线程的工作。它允许创建并访问多线程应用程序中的单个线程。进程中第一个被执行的线程称为主线程。

当 C# 程序开始执行时，主线程自动创建。使用 Thread 类创建的线程被主线程的子线程调用。您可以使用 Thread 类的 CurrentThread 属性访问线程。

下面的程序演示了主线程的执行：


## 实例

当上面的代码被编译和执行时，它会产生下列结果：

```text
This is MainThread
```


## Thread 类常用的属性和方法

下表列出了 Thread 类的一些常用的 属性：

下表列出了 Thread 类的一些常用的 方法：


## 创建线程

线程是通过扩展 Thread 类创建的。扩展的 Thread 类调用 Start() 方法来开始子线程的执行。

下面的程序演示了这个概念：


## 实例

当上面的代码被编译和执行时，它会产生下列结果：

```text
In Main: Creating the Child thread
Child thread starts
```


## 管理线程

Thread 类提供了各种管理线程的方法。

下面的实例演示了 sleep() 方法的使用，用于在一个特定的时间暂停线程。


## 实例

当上面的代码被编译和执行时，它会产生下列结果：

```text
In Main: Creating the Child thread
Child thread starts
Child Thread Paused for 5 seconds
Child thread resumes
```


## 销毁线程

Abort() 方法用于销毁线程。

通过抛出 threadabortexception 在运行时中止线程。这个异常不能被捕获，如果有 finally 块，控制会被送至 finally 块。

下面的程序说明了这点：


## 实例

当上面的代码被编译和执行时，它会产生下列结果：

```text
In Main: Creating the Child thread
Child thread starts
0
1
2
In Main: Aborting the Child thread
Thread Abort Exception
Couldn't catch the Thread Exception
```


## 记忆卡片

- 一句话定义：`C# 多线程` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
