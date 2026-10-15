# C++：C++ 标准库 <complex>

- 来源：[C++ <complex>](https://www.runoob.com/cplusplus/cpp-libs-complex.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：学习笔记
- 章节序号：3605

## 本章内容

在数学和工程计算中，我们常常需要处理 复数（complex number），比如信号处理、傅里叶变换、电路分析等。

C++ 标准库提供了 <complex> 头文件，让你可以像处理普通数字一样轻松操作复数。

一个复数由实部（real part）和虚部（imaginary part）构成，形式：

```text
z = a + bi
```

复数是实数和虚数的组合，通常表示为 a + bi，其中 a 是实部，b 是虚部，i 是虚数单位，满足 i^2 = -1。

在 C++ 中，复数类型由 std::complex<T> 表示，其中 T 可以是任意的算术类型，如 float、double 或 long double。

要使用 <complex> 库，首先需要在你的 C++ 程序中包含这个头文件：

```html
#include <iostream>
#include <complex>
```


## 实例

输出：

```text
z1 = (3,4)
z2 = (1,-2)
```


## 基本语法


### 创建复数

```html
std::complex<double> c(5.0, 3.0); // 创建一个复数 5 + 3i
```


### 访问实部和虚部

```text
double realPart = c.real(); // 获取实部
double imagPart = c.imag(); // 获取虚部
```


### 复数的基本运算

C++ 标准库 <complex> 支持以下基本运算：

- 加法：operator+
- 减法：operator-
- 乘法：operator*
- 除法：operator/
- 共轭：conj
- 模：abs
- 辐角：arg

1 、获取实部和虚部

```text
std::cout << "实部: " << z1.real() << std::endl; // 3
std::cout << "虚部: " << z1.imag() << std::endl; // 4
```

2、四则运算：


## 实例

3、常用函数

头文件 <complex> 提供了很多和复数相关的数学函数。


## 实例

4、极坐标表示

有时我们需要用 极坐标（模长 + 相角） 表示复数。


## 实例

std::complex<T> 是一个模板类，支持不同的数值类型：

- std::complex<float>
- std::complex<double>（常用）
- std::complex<long double>


## 实例


## 实例

下面是一个使用 <complex> 头文件的简单示例，包括创建复数、基本运算和输出结果。


## 实例

当你运行上述程序时，你将得到以下输出：

```text
c1: (5,3)
c2: (2,-4)
Sum: (7,-1)
Difference: (3,7)
Product: (22,-14)
Quotient: (-0.1,1.3)
Conjugate of c1: (5,-3)
Modulus of c1: 5.83095
Argument of c1: 0.54042
```


## 复习重点

- 能说明 `C++ <complex>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
