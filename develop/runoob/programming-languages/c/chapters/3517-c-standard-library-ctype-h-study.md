# C：C 标准库 - <ctype.h>

- 来源：[C 标准库 - <ctype.h>](https://www.runoob.com/cprogramming/c-standard-library-ctype-h.html)
- 分类：编程语言
- 技术：C
- 笔记类型：学习笔记
- 章节序号：3517

## 本章内容

## 简介

C 标准库的 ctype.h 头文件提供了一些函数，可用于测试和转换字符，这些函数主要用于检查字符的类型（如字母、数字、空白字符等）以及进行字符大小写转换。

<ctype.h> 提供了一组方便的函数，用于处理字符的分类和转换操作，是 C 标准库中处理字符操作的重要工具。

以下是一个简单的示例，演示了如何使用 <ctype.h> 提供的函数：


## 实例

输出结果为：

```text
Character: 'a'
 - isalpha: Yes
 - isdigit: No
 - isspace: No
 - isprint: Yes
 - ispunct: No
Character: '1'
 - isalpha: No
 - isdigit: Yes
 - isspace: No
 - isprint: Yes
 - ispunct: No
Character: ' '
 - isalpha: No
 - isdigit: No
 - isspace: Yes
 - isprint: Yes
 - ispunct: No
Character: 'B'
 - isalpha: Yes
 - isdigit: No
 - isspace: No
 - isprint: Yes
 - ispunct: No
Character: '?'
 - isalpha: No
 - isdigit: No
 - isspace: No
 - isprint: Yes
 - ispunct: Yes
Character: '
'
 - isalpha: No
 - isdigit: No
 - isspace: Yes
 - isprint: No
 - ispunct: No
tolower('A') = 'a'
toupper('a') = 'A'
```


## 库函数

下面列出了头文件 ctype.h 中定义的函数。

这些函数用于测试字符是否属于某种类型，这些函数接受 int 作为参数，它的值必须是 EOF 或表示为一个无符号字符。

如果参数 c 满足描述的条件，则这些函数返回非零（true）。如果参数 c 不满足描述的条件，则这些函数返回零。

标准库还包含了两个转换函数，它们接受并返回一个 "int"


## 字符类


## 复习重点

- 能说明 `C 标准库 - <ctype.h>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
