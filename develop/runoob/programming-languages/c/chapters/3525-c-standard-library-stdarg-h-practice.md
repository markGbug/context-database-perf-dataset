# C：C 标准库 - <stdarg.h>

- 来源：[C 标准库 - <stdarg.h>](https://www.runoob.com/cprogramming/c-standard-library-stdarg-h.html)
- 分类：编程语言
- 技术：C
- 笔记类型：练习笔记
- 章节序号：3525

## 本章内容

<stdarg.h> 是 C 标准库中的一个头文件，提供了一组宏，用于访问可变数量的参数。

stdarg.h 头文件定义了一个变量类型 va_list 和三个宏，这三个宏可用于在参数个数未知（即参数个数可变）时获取函数中的参数。

可变参数的函数通在参数列表的末尾是使用省略号 ... 定义的。


## 库变量

下面是头文件 stdarg.h 中定义的变量类型：


## 库宏

下面是头文件 stdarg.h 中定义的宏：


### 实例

以下是一个使用 <stdarg.h> 实现可变参数函数的示例。该函数计算所有参数的总和：


## 实例

输出结果:

```text
Sum of 1, 2, 3: 6
Sum of 4, 5, 6, 7: 22
```


### 解析

- va_list args;：声明一个 va_list 变量，用于访问可变参数。
- va_start(args, count);：初始化 args 以遍历可变参数列表，从 count 之后的第一个参数开始。
- total += va_arg(args, int);：获取可变参数列表中的下一个参数，并将其累加到 total 中。参数类型为 int。
- va_end(args);：清理 args。


### 注意事项

- 可变参数列表中的每个参数类型必须明确，且必须一致地传递给 va_arg。
- 使用 va_start 后，必须使用 va_end 清理 va_list 变量。
- va_start、va_arg 和 va_end 宏在一个函数中应成对使用，以避免未定义行为。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C 标准库 - <stdarg.h>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
