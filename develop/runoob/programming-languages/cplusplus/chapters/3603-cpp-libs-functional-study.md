# C++：C++ 标准库 <functional>

- 来源：[C++ <functional>](https://www.runoob.com/cplusplus/cpp-libs-functional.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：学习笔记
- 章节序号：3603

## 本章内容

C++ 标准库中的 <functional> 头文件提供了一组函数模板，这些模板允许我们使用函数对象（function objects）作为参数传递给算法，或者作为算法的返回值。函数对象是那些重载了 operator() 的对象，它们可以像普通函数一样被调用。

在 C++ 中，函数对象是一种特殊的类，它重载了 operator() 来允许对象像函数一样被调用。这使得我们可以将行为作为对象传递，增加了代码的灵活性和可重用性。


## 语法

要使用 <functional> 头文件中的功能，你需要在你的 C++ 程序中包含这个头文件：

```html
#include <functional>
```


## 常用函数对象

<functional> 头文件中定义了一些常用的函数对象，包括：

- std::function：一个通用的多态函数封装器。
- std::bind：用于绑定函数的参数。
- std::plus、std::minus、std::multiplies、std::divides、std::modulus：基本的算术操作。
- std::equal_to、std::not_equal_to、std::greater、std::less、std::greater_equal、std::less_equal：比较操作。
- std::unary_negate、std::binary_negate：逻辑否定操作。
- std::logical_and、std::logical_or、std::logical_not：逻辑操作。


## 实例


### 使用 std::function

std::function 是一个模板类，可以存储、调用和复制任何可调用对象，比如函数、lambda 表达式或函数对象。


## 实例


### 使用 std::bind

std::bind 允许我们创建一个可调用对象，它在调用时会将给定的参数绑定到一个函数或函数对象。


## 实例

在这个例子中，std::placeholders::_1 是一个占位符，它在调用 bound_add 时会被实际的参数替换。


### 使用比较函数对象

比较函数对象可以用于算法，比如 std::sort。


## 实例

<functional> 头文件是 C++ 标准库中一个非常强大的部分，它提供了丰富的函数对象和工具，使得我们可以编写更灵活、更可重用的代码。通过使用函数对象，我们可以将行为作为参数传递，或者将它们存储在容器中，从而实现更高级的编程技术。


## 复习重点

- 能说明 `C++ <functional>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
