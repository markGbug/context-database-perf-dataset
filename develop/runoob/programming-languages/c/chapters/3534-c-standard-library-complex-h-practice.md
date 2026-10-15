# C：C 标准库 <complex.h>

- 来源：[C 标准库 <complex.h>](https://www.runoob.com/cprogramming/c-standard-library-complex-h.html)
- 分类：编程语言
- 技术：C
- 笔记类型：练习笔记
- 章节序号：3534

## 本章内容

<complex.h> 是 C 标准库中的一个头文件，用于支持复数运算。

<complex.h> 在 C99 标准中引入，提供了一组用于定义和操作复数的类型、宏和函数。


### 1、复数类型

<complex.h> 定义了以下复数类型：

- float complex：单精度复数。
- double complex：双精度复数。
- long double complex：长双精度复数。

这些类型实际上是 C 标准库中定义的宏，分别扩展为 _Complex float、_Complex double 和 _Complex long double。


### 2、复数常量

<complex.h> 定义了以下宏，用于表示虚数单位 i：

- I：表示虚数单位 i，即 sqrt(-1)。


## 实例


### 3、复数操作函数

<complex.h> 提供了一组用于操作复数的函数，包括算术运算、三角函数、指数函数和对数函数等。以下是一些常用函数：


### 4、实例

以下是一个使用 <complex.h> 的示例，展示了如何定义和操作复数：


## 实例

输出结果：

```text
z1 = 3.00 + 4.00i
z2 = 1.00 + -2.00i
Sum = 4.00 + 2.00i
Product = 11.00 + -2.00i
|z1| = 5.00
Phase of z1 = 0.93 radians
exp(z1) = -13.13 + -15.20i
```


### 5、注意事项

- <complex.h> 仅在 C99 及更高版本中可用。
- 复数类型和函数的使用需要包含 <complex.h> 头文件。
- 复数运算的性能可能低于实数运算，特别是在涉及大量计算时。


### 6、复数运算的数学背景

复数的一般形式为 a + bi，其中：

- a 是实部，b 是虚部。
- i 是虚数单位，满足 i² = -1。

复数的模（绝对值）为：

```text
|z| = sqrt(a² + b²)
```

复数的幅角（相位）为：

```text
arg(z) = atan2(b, a)
```

复数的指数形式为：

```text
exp(z) = exp(a) * (cos(b) + i * sin(b))
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C 标准库 <complex.h>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
