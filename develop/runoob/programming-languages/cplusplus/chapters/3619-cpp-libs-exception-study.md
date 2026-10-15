# C++：C++ 标准库 <exception>

- 来源：[C++ <exception>](https://www.runoob.com/cplusplus/cpp-libs-exception.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：学习笔记
- 章节序号：3619

## 本章内容

在 C++ 编程中，异常处理是一种重要的错误处理机制，它允许程序在遇到错误时，能够优雅地处理这些错误，而不是让程序崩溃。

在 C++ 中，异常处理通常使用 try、catch 和 throw 关键字来实现。标准库中提供了 std::exception 类及其派生类来处理异常。

C++ 标准库中的 <exception> 头文件提供了一套异常处理的基础设施，包括异常类、异常处理机制等。

异常是程序运行时发生的一个事件，它中断了正常的指令流程。在C++中，异常可以是任何类型的对象，但通常是一个异常类的对象。C++标准库定义了一些基本的异常类，如 std::exception、std::bad_alloc、std::bad_cast 等。

你可以通过定义自己的异常类来扩展异常处理功能，或者使用标准库中已有的异常类来处理常见的异常情况。


### 语法

抛出异常

在 C++ 中，使用 throw 关键字来抛出一个异常，语法如下：

```text
throw exception_object;
```

捕获异常

使用 try 和 catch 关键字来捕获和处理异常，语法如下：

```text
try {
    // 可能抛出异常的代码
} catch (exception_type e) {
    // 处理异常的代码
}
```

可以指定捕获的异常类型，也可以使用通用的 catch 块捕获所有类型的异常:

```javascript
try {
    // 可能会抛出异常的代码
} catch (const std::exception& e) {
    // 处理 std::exception 及其派生类的异常
} catch (...) {
    // 处理所有其他类型的异常
}
```

std::exception

std::exception 是 C++ 标准库中定义的基类，用于所有标准异常类的基础。它定义了一些虚函数，如 what()，用于返回异常信息的 C 风格字符串。

```javascript
class exception {
public:
    virtual const char* what() const noexcept;
};
```

标准异常类

C++ 标准库提供了多个派生自 std::exception 的异常类，如 std::runtime_error、std::logic_error 等，用于表示常见的异常情况。你可以根据具体的异常情况选择合适的类来使用。

```text
throw std::runtime_error("Runtime error occurred");
throw std::logic_error("Logic error occurred");
```


## 实例

下面是一个使用 <exception> 头文件的简单示例，演示了如何抛出和捕获异常。


## 实例

输出结果：

```text
Caught an exception: My custom exception
```


## 异常类

在 C++ 中，标准库提供了一些常用的异常类，它们都继承自 std::exception，并且可以通过 #include <stdexcept> 引入使用。

以下是一些常见的 C++ 异常类及其主要用途：

- std::exception: 所有标准异常类的基类，定义了异常的基本接口。它有一个虚函数 what()，用于返回异常信息的 C 风格字符串。
- std::runtime_error: 表示运行时错误，通常是由于程序逻辑问题导致的异常，例如无效的参数、无法打开文件等。 throw std::runtime_error("Runtime error occurred");
- std::logic_error: 表示逻辑错误，通常是由于程序逻辑错误导致的异常，例如逻辑断言失败、索引越界等。 throw std::logic_error("Logic error occurred");
- std::invalid_argument: 表示传递给函数的参数无效。 throw std::invalid_argument("Invalid argument");
- std::out_of_range: 表示访问超出有效范围的对象，如数组、容器等。 throw std::out_of_range("Out of range");
- std::overflow_error 和 std::underflow_error: 表示数值计算时出现溢出或下溢。 throw std::overflow_error("Overflow occurred"); throw std::underflow_error("Underflow occurred");
- std::bad_alloc: 表示内存分配失败。 throw std::bad_alloc(); // 内存分配失败时抛出


## 实例

输出：

```text
Memory allocation failed: std::bad_alloc
```


## 注意事项

- 异常不应该用于正常的控制流，它们应该只用于处理异常情况。
- 异常处理可能会影响程序的性能，因此应该谨慎使用。
- 确保在 catch 块中处理所有可能的异常类型，以避免程序在未处理的异常中崩溃。

通过使用 <exception> 头文件，C++ 程序员可以更有效地处理程序中的错误情况，提高程序的健壮性和可靠性。


## 复习重点

- 能说明 `C++ <exception>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
