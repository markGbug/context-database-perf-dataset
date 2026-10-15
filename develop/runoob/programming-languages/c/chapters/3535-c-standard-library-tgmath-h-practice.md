# C：C 标准库 <tgmath.h>

- 来源：[C 标准库 <tgmath.h>](https://www.runoob.com/cprogramming/c-standard-library-tgmath-h.html)
- 分类：编程语言
- 技术：C
- 笔记类型：练习笔记
- 章节序号：3535

## 本章内容

<tgmath.h> 是 C 标准库中的一个头文件，提供了类型泛型数学函数（Type-Generic Math Functions）。

<tgmath.h> 库在 C99 标准中引入，允许开发者使用统一的函数名来调用不同类型的数学函数（如 float、double 和 long double），而无需显式指定函数的具体类型。

<tgmath.h> 的主要目的是：

- 简化数学函数的使用，避免为不同类型（如 float、double、long double）显式调用不同的函数（如 sinf、sin、sinl）。
- 提高代码的可读性和可维护性。
- 支持复数类型的数学函数。


### 1、类型泛型宏

<tgmath.h> 定义了一组类型泛型宏，这些宏根据参数的类型自动选择正确的数学函数。例如：

- sin(x)：如果 x 是 float，则调用 sinf(x)；如果 x 是 double，则调用 sin(x)；如果 x 是 long double，则调用 sinl(x)。
- sqrt(x)：如果 x 是 float，则调用 sqrtf(x)；如果 x 是 double，则调用 sqrt(x)；如果 x 是 long double，则调用 sqrtl(x)。

这些宏支持以下类型的参数：

- 实数类型：float、double、long double。
- 复数类型：float complex、double complex、long double complex。


### 2、支持的函数

<tgmath.h> 支持以下类型泛型数学函数：


### 3、实例

以下是一个使用 <tgmath.h> 的示例，展示了如何使用类型泛型数学函数：


## 实例

输出结果：

```text
sin(f) = 0.997495
sin(d) = 0.598472
sin(ld) = 0.350783
sqrt(z) = 1.272020 + 0.786151i
```


### 4、注意事项

- <tgmath.h> 仅在 C99 及更高版本中可用。
- 类型泛型宏根据参数的类型自动选择正确的函数，因此参数的类型必须明确。
- 如果参数类型不明确（例如，整数常量），编译器可能会选择默认的 double 版本。
- 复数类型的函数需要包含 <complex.h> 头文件。


### 5、实现原理

<tgmath.h> 的实现依赖于 C 语言的泛型选择机制（_Generic 关键字）。例如，sin 宏的定义可能如下：

```text
#define sin(x) _Generic((x), \
    float: sinf,             \
    double: sin,             \
    long double: sinl        \
)(x)
```

_Generic 关键字根据 x 的类型选择正确的函数。

<tgmath.h> 提供了类型泛型数学函数，简化了不同数值类型（如 float、double、long double 和复数类型）的数学函数调用。它是 C99 标准中的一个重要特性，特别适用于需要处理多种数值类型的科学计算和工程应用。通过使用 <tgmath.h>，开发者可以编写更简洁、更通用的代码。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C 标准库 <tgmath.h>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
