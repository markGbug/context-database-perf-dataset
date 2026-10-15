# C：C 标准库 - <setjmp.h>

- 来源：[C 标准库 - <setjmp.h>](https://www.runoob.com/cprogramming/c-standard-library-setjmp-h.html)
- 分类：编程语言
- 技术：C
- 笔记类型：学习笔记
- 章节序号：3523

## 本章内容

## 简介

setjmp.h 头文件定义了宏 setjmp()、函数 longjmp() 和变量类型 jmp_buf，该变量类型会绕过正常的函数调用和返回规则。

<setjmp.h> 是 C 标准库中的一个头文件，提供了一组函数和宏，用于非本地跳转（即从一个函数跳转到另一个之前调用过的函数，而不需要正常的函数返回机制）。这种机制通常用于错误处理、异常处理或者跳出深层嵌套的循环或递归。


## 库变量

下面列出了头文件 setjmp.h 中定义的变量：

jmp_buf 是一个数据类型，用于保存调用环境，包括栈指针、指令指针和寄存器等。在执行 setjmp() 时，这些环境信息会被保存到 jmp_buf 类型的变量中。


## 库宏

下面是这个库中定义的唯一的一个宏：


## 库函数

下面是头文件 setjmp.h 中定义的唯一的一个函数：


### 实例

以下示例展示了如何使用 setjmp() 和 longjmp() 实现非本地跳转：


## 实例

运行上述程序将输出类似以下内容：

```text
Starting main()
Entering first()
Calling second() from first()
Entering second()
Returned to first() from second() using longjmp
Exiting first()
Exiting main()
```


### 代码解析

- jmp_buf env：定义一个用于保存环境信息的变量 env。
- first() 函数：调用 setjmp(env) 保存当前环境信息，并根据其返回值决定是否调用 second() 函数。
- second() 函数：调用 longjmp(env, 1)，跳转回 setjmp(env)，并使其返回 1。
- main() 函数：调用 first() 函数。


### 使用场景

- 错误处理：在深层嵌套的函数调用中使用 setjmp() 和 longjmp() 实现错误处理机制。
- 异常处理：用于实现简单的异常处理。
- 中断控制流：在某些情况下，可以中断正常的控制流，跳出多层嵌套的循环或函数调用。


### 注意事项

- 使用 setjmp() 和 longjmp() 需要小心，因为它们会跳过正常的栈展开过程，可能导致资源泄漏（如未释放的内存、未关闭的文件等）。
- 避免在调用 setjmp() 和 longjmp() 之间修改局部变量，因为这可能导致未定义行为。
- 非本地跳转可能使代码难以阅读和调试，因此应谨慎使用。


### 总结

<setjmp.h> 提供了 setjmp() 和 longjmp() 函数，用于实现非本地跳转。这些函数在错误处理和异常处理中非常有用，但需要谨慎使用以避免潜在的问题。


## 复习重点

- 能说明 `C 标准库 - <setjmp.h>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
