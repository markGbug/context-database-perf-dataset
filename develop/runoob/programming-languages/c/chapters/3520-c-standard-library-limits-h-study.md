# C：C 标准库 - <limits.h>

- 来源：[C 标准库 - <limits.h>](https://www.runoob.com/cprogramming/c-standard-library-limits-h.html)
- 分类：编程语言
- 技术：C
- 笔记类型：学习笔记
- 章节序号：3520

## 本章内容

## 简介

<limits.h> 是 C 标准库中的一个头文件，定义了各种数据类型的限制。这些宏提供了有关整数类型（char、short、int、long 和 long long 等）和其他数据类型的最大值和最小值的信息。

这些限制指定了变量不能存储任何超出这些限制的值，例如一个无符号可以存储的最大值是 255。


## 库宏

下面的值是特定实现的，且是通过 #define 指令来定义的，这些值都不得低于下边所给出的值。


## 实例

下面的实例演示了 limit.h 文件中定义的一些常量的使用。


## 实例

让我们编译和运行上面的程序，这将产生下列结果：

```text
Character types:
CHAR_BIT: 8
CHAR_MIN: -128
CHAR_MAX: 127
SCHAR_MIN: -128
SCHAR_MAX: 127
UCHAR_MAX: 255

Short integer types:
SHRT_MIN: -32768
SHRT_MAX: 32767
USHRT_MAX: 65535

Integer types:
INT_MIN: -2147483648
INT_MAX: 2147483647
UINT_MAX: 4294967295

Long integer types:
LONG_MIN: -9223372036854775808
LONG_MAX: 9223372036854775807
ULONG_MAX: 18446744073709551615

Long long integer types:
LLONG_MIN: -9223372036854775808
LLONG_MAX: 9223372036854775807
ULLONG_MAX: 18446744073709551615
```

<limits.h> 提供了许多与整数类型相关的宏，用于描述各种数据类型的限制。这些宏对于编写健壮和移植性强的代码非常有用，因为它们允许程序员在不同平台上轻松获取数据类型的限制值。


## 复习重点

- 能说明 `C 标准库 - <limits.h>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
