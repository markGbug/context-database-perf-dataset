# C++：C++ 标准库 <cwchar>

- 来源：[C++ <cwchar>](https://www.runoob.com/cplusplus/cpp-libs-cwchar.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：练习笔记
- 章节序号：3630

## 本章内容

<cwchar> 是 C++ 标准库中的一个头文件，提供了处理宽字符（wchar_t）和宽字符串的函数。这些函数大部分来自 C 标准库的 <wchar.h>，用于处理宽字符的输入输出、内存操作、字符串操作和其他与宽字符相关的功能。


## 语法

cwchar 头文件中定义的函数通常具有与标准字符处理函数相似的名称，但以 w 开头，例如 wprintf、wscanf 等。这些函数的参数和返回类型也与相应的标准字符函数不同，它们使用宽字符类型 wchar_t。


### 基本类型

- wchar_t：宽字符类型，用于存储宽字符。
- wint_t：用于存储宽字符函数的返回值。


## 常用函数


### 1. 宽字符输入输出

- fgetwc：从文件流中读取宽字符。
- fputwc：向文件流中写入宽字符。
- fgetws：从文件流中读取宽字符串。
- fputws：向文件流中写入宽字符串。


## 实例

输出结果为：

```text
Read from file: Hello, 世界!
```


### 2. 宽字符和宽字符串操作

- wcscpy：拷贝宽字符串。
- wcslen：获取宽字符串长度。
- wcscmp：比较宽字符串。
- wcsncpy：拷贝指定长度的宽字符串。


## 实例

输出结果为：

```text
Copied string: Hello,
```


### 3. 宽字符分类和转换

- iswalpha：判断宽字符是否为字母。
- iswdigit：判断宽字符是否为数字。
- towlower：将宽字符转换为小写。
- towupper：将宽字符转换为大写。


## 实例

输出结果为：

```text
A is an alphabetic character.
9 is a digit.
Lowercase of G is g
Uppercase of a is A
```


### 4. 宽字符和宽字符串的输入输出

- wprintf：宽字符格式化输出。
- wscanf：宽字符格式化输入。
- swprintf：将格式化宽字符写入宽字符串。
- swscanf：从宽字符串中读取格式化宽字符。


## 实例

输出结果为：

```text
Formatted output: 42 H
Enter a number and a string: runoob
You entered:
Buffer: Formatted 42 o
Parsed number: 42, word: o
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C++ <cwchar>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
