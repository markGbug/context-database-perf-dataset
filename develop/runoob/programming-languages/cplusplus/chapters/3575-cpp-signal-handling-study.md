# C++：C++ 信号处理

- 来源：[C++ 信号处理](https://www.runoob.com/cplusplus/cpp-signal-handling.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：学习笔记
- 章节序号：3575

## 本章内容

信号是由操作系统传给进程的中断，会提早终止一个程序。在 UNIX、LINUX、Mac OS X 或 Windows 系统上，可以通过按 Ctrl+C 产生中断。

有些信号不能被程序捕获，但是下表所列信号可以在程序中捕获，并可以基于信号采取适当的动作。这些信号是定义在 C++ 头文件 <csignal> 中。


## signal() 函数

C++ 信号处理库提供了 signal 函数，用来捕获突发事件。以下是 signal() 函数的语法：

```java
void (*signal (int sig, void (*func)(int)))(int);
```

这个看起来有点费劲，以下语法格式更容易理解：

```text
signal(registered signal, signal handler)
```

这个函数接收两个参数：第一个参数是要设置的信号的标识符，第二个参数是指向信号处理函数的指针。函数返回值是一个指向先前信号处理函数的指针。如果先前没有设置信号处理函数，则返回值为 SIG_DFL。如果先前设置的信号处理函数为 SIG_IGN，则返回值为 SIG_IGN。

让我们编写一个简单的 C++ 程序，使用 signal() 函数捕获 SIGINT 信号。不管您想在程序中捕获什么信号，您都必须使用 signal 函数来注册信号，并将其与信号处理程序相关联。看看下面的实例：


## 实例

```java
#include <iostream>
#include <csignal>
#include <unistd.h>

using namespace std;

void signalHandler( int signum )
{
    cout << "Interrupt signal (" << signum << ") received.\n";

    // 清理并关闭
    // 终止程序

   exit(signum);

}

int main ()
{
    // 注册信号 SIGINT 和信号处理程序
    signal(SIGINT, signalHandler);

    while(1){
       cout << "Going to sleep...." << endl;
       sleep(1);
    }

    return 0;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```text
Going to sleep....
Going to sleep....
Going to sleep....
```

现在，按 Ctrl+C 来中断程序，您会看到程序捕获信号，程序打印如下内容并退出：

```text
Going to sleep....
Going to sleep....
Going to sleep....
Interrupt signal (2) received.
```


## raise() 函数

您可以使用函数 raise() 生成信号，该函数带有一个整数信号编号作为参数，语法如下：

```java
int raise (signal sig);
```

在这里，sig 是要发送的信号的编号，这些信号包括：SIGINT、SIGABRT、SIGFPE、SIGILL、SIGSEGV、SIGTERM、SIGHUP。以下是我们使用 raise() 函数内部生成信号的实例：


## 实例

```java
#include <iostream>
#include <csignal>
#include <unistd.h>

using namespace std;

void signalHandler( int signum )
{
    cout << "Interrupt signal (" << signum << ") received.\n";

    // 清理并关闭
    // 终止程序

   exit(signum);

}

int main ()
{
    int i = 0;
    // 注册信号 SIGINT 和信号处理程序
    signal(SIGINT, signalHandler);

    while(++i){
       cout << "Going to sleep...." << endl;
       if( i == 3 ){
          raise( SIGINT);
       }
       sleep(1);
    }

    return 0;
}
```

当上面的代码被编译和执行时，它会产生下列结果，并会自动退出：

```text
Going to sleep....
Going to sleep....
Going to sleep....
Interrupt signal (2) received.
```


## 复习重点

- 能说明 `C++ 信号处理` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
