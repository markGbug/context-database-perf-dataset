# C++：C++ 标准库 <chrono>

- 来源：[C++ <chrono>](https://www.runoob.com/cplusplus/cpp-libs-chrono.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：练习笔记
- 章节序号：3611

## 本章内容

C++11 引入了 <chrono> 库，这是一个用于处理时间和日期的库。它提供了一套丰富的工具来测量时间间隔、执行时间点的计算以及处理日期和时间。<chrono> 库是 C++ 标准库中处理时间相关操作的核心部分。


## 基本概念


### 时间点（Time Points）

时间点表示一个特定的时间点，通常与某个特定的时钟相关联。


### 持续时间（Durations）

持续时间表示两个时间点之间的时间间隔。


### 时钟（Clocks）

时钟是时间点和持续时间的来源。C++ 提供了几种不同的时钟，例如系统时钟、高分辨率时钟等。


## 基本语法


### 包含头文件

在使用 <chrono> 库之前，需要包含相应的头文件：

```html
#include <chrono>
```


### 使用时间点

```text
auto now = std::chrono::system_clock::now();
```


### 使用持续时间

```text
auto duration = std::chrono::seconds(5);
```


### 计算时间点

```text
auto future_time = now + duration;
```


## 实例


### 测量函数执行时间

下面是一个使用 <chrono> 库测量函数执行时间的简单示例：


## 实例

输出结果：

```text
Function took 1000 milliseconds to execute.
```


### 处理日期和时间

<chrono> 库也可以用来处理日期和时间。下面是一个使用 std::chrono::system_clock 和 std::chrono::time_point 来获取当前日期和时间的示例：


## 实例

输出结果：

```text
Current date and time: Fri Mar 11 12:34:56 2022
```


## 高级用法


### 使用不同的时钟

C++ 提供了多种时钟，例如：

- std::chrono::system_clock：系统时钟，通常与系统时间同步。
- std::chrono::steady_clock：单调时钟，不会受到系统时间变化的影响。
- std::chrono::high_resolution_clock：提供最高分辨率的时钟。


### 格式化日期和时间

可以使用 <iomanip> 和 <ctime> 来格式化日期和时间：


## 实例

输出结果：

```text
2022-03-11 12:34:56
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C++ <chrono>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
