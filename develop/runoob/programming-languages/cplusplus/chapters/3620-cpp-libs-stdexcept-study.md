# C++：C++ 异常处理库 <stdexcept>

- 来源：[C++ <stdexcept>](https://www.runoob.com/cplusplus/cpp-libs-stdexcept.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：学习笔记
- 章节序号：3620

## 本章内容

<stdexcept> 是 C++ 标准库中的一个头文件，它定义了一组标准异常类，用于处理程序运行时的错误情况。

异常是程序运行时发生的错误，它们可以被捕获并处理，以避免程序的非正常终止。<stdexcept> 头文件定义了一组从 std::exception 派生的异常类，这些类提供了一种标准的方式来报告和处理错误。


### 语法

要使用 <stdexcept> 中的异常类，首先需要包含这个头文件：

```html
#include <stdexcept>
```

然后，你可以使用这些异常类来抛出和捕获异常。例如：

```text
throw std::runtime_error("An error occurred");
```


### 异常类

<stdexcept> 头文件定义了以下异常类：

- std::exception：所有标准异常类的基类。
- std::bad_exception：当异常处理过程中发生错误时抛出。
- std::bad_alloc：当内存分配失败时抛出。
- std::bad_cast：当类型转换失败时抛出。
- std::bad_typeid：当 typeid 操作失败时抛出。
- std::logic_error：当逻辑错误发生时抛出，例如无效的输入参数。
- std::domain_error：当函数调用的参数不在有效范围内时抛出。
- std::invalid_argument：当函数调用的参数无效时抛出。
- std::length_error：当容器操作因为长度限制而失败时抛出。
- std::out_of_range：当访问容器的非法索引时抛出。
- std::overflow_error：当算术运算导致溢出时抛出。
- std::range_error：当函数返回值不在期望的范围内时抛出。
- std::underflow_error：当算术运算导致下溢时抛出。


## 实例

下面是一个使用 <stdexcept> 的简单示例，演示了如何抛出和捕获异常：


## 实例

输出结果:

```text
Caught an exception: Negative value not allowed
```

在这个示例中，riskyFunction 函数检查传入的参数是否为负数，如果是，则抛出 std::invalid_argument 异常。在 main 函数中，我们使用 try-catch 块来捕获并处理这个异常。


## 标准异常类


### std::exception

std::exception 是所有标准异常类的基类。它提供了一个虚函数 what()，用于返回描述异常的字符串。


## 实例


### std::logic_error

std::logic_error 派生自 std::exception，表示程序逻辑错误。它是一个抽象基类，通常由派生类来具体化。


## 实例


### std::invalid_argument

std::invalid_argument 派生自 std::logic_error，表示传递了无效的参数。


## 实例


### std::domain_error

std::domain_error 派生自 std::logic_error，表示参数超出了有效范围。


## 实例


### std::length_error

std::length_error 派生自 std::logic_error，表示长度错误，如在容器操作中超出了最大长度限制。


## 实例


### std::out_of_range

std::out_of_range 派生自 std::logic_error，表示访问超出了有效范围。


## 实例


### std::runtime_error

std::runtime_error 派生自 std::exception，表示程序运行时错误。它是一个抽象基类，通常由派生类来具体化。


## 实例


### std::range_error

std::range_error 派生自 std::runtime_error，表示计算结果超出了表示范围。


## 实例


### std::overflow_error

std::overflow_error 派生自 std::runtime_error，表示算术溢出错误。


## 实例


### std::underflow_error

std::underflow_error 派生自 std::runtime_error，表示算术下溢错误。


## 后续章节

- 实例
- 使用自定义异常类
- 实例

## 复习重点

- 能说明 `C++ <stdexcept>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
