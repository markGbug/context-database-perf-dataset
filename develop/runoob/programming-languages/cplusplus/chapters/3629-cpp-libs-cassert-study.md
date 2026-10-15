# C++：C++ 标准库中的 <cassert>

- 来源：[C++ <cassert>](https://www.runoob.com/cplusplus/cpp-libs-cassert.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：学习笔记
- 章节序号：3629

## 本章内容

<cassert> 是 C++ 标准库中的一个头文件，它提供了断言功能，用于在程序运行时检查条件是否为真。如果条件为假，程序将终止执行，并输出一条错误信息。断言主要用于调试阶段，以确保程序的逻辑正确性。

断言是一种调试工具，用于在开发过程中检查程序的运行状态。如果断言失败，程序将立即终止，这有助于开发者快速定位问题。


## 语法

cassert 中的 assert 宏的基本语法如下：

```html
#include <cassert>

assert(expression);
```

其中 expression 是一个布尔表达式，如果表达式的结果为 true，则程序继续执行；如果结果为 false，则程序将终止，并输出一条错误信息。


## 实例

下面是一个使用 cassert 的简单示例：


## 实例


### 输出结果

当运行上述程序时，由于 a 确实大于 b，所以程序将正常执行，并输出：

```text
a is greater than b
```

如果我们修改 a 的值为 2，使其不大于 b，程序将输出错误信息并终止：

```text
Assertion failed: a > b, file main.cpp, line 8.
```


## 断言的高级用法

assert 宏还可以接受一个额外的表达式，用于输出自定义的错误信息：


## 实例

当运行上述程序时，由于 y 为 0，断言将失败，并输出：

```text
Division by zero error
Assertion failed: y != 0 && "Division by zero error", file main.cpp, line 8.
```


### 注意事项

- 在发布版本的程序中，通常需要禁用断言，以避免程序在运行时意外终止。这可以通过定义 NDEBUG 宏来实现： #define NDEBUG #include <cassert>
- 断言应该只用于检查程序的逻辑错误，而不是用于处理运行时的错误。运行时错误应该通过异常处理或其他机制来处理。
- 断言的表达式应该是简单的，避免使用复杂的逻辑或计算，以减少性能开销。

通过使用 cassert 中的 assert 宏，开发者可以在开发过程中快速发现并修复逻辑错误，提高程序的稳定性和可靠性。


## 复习重点

- 能说明 `C++ <cassert>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
