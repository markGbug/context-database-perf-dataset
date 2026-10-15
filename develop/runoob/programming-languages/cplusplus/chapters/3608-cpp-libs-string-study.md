# C++：C++ 标准库 <string>

- 来源：[C++ <string>](https://www.runoob.com/cplusplus/cpp-libs-string.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：学习笔记
- 章节序号：3608

## 本章内容

C++ 标准库（Standard Template Library, STL）是 C++ 的核心组成部分之一，提供了丰富的数据结构和算法。

<string> 是 C++ 标准库中用于处理字符串的头文件。

在 C++ 中，字符串是由字符组成的序列。<string> 头文件提供了 std::string 类，它是对 C 风格字符串的封装，提供了更安全、更易用的字符串操作功能。

要在 C++ 程序中使用 <string> 库，首先需要包含这个头文件：

```html
#include <iostream>
#include <string>
```


## 基本语法

std::string 类的基本语法如下：

- 声明字符串变量： std::string str;
- 初始化字符串： std::string str = "Hello, World!";
- 使用 + 连接字符串： std::string str1 = "Hello, "; std::string str2 = "World!"; std::string result = str1 + str2;


## 常用成员函数

std::string 类提供了许多成员函数来操作字符串，以下是一些常用的成员函数：

- size()：返回字符串的长度。
- empty()：检查字符串是否为空。
- operator[]：通过索引访问字符串中的字符。
- substr()：获取子字符串。
- find()：查找子字符串在主字符串中的位置。
- replace()：替换字符串中的某些字符。


## 实例

下面是一个使用 <string> 库的简单实例，包括输出结果：


## 实例

输出结果:

```text
Length of the greeting: 13
Is the greeting empty? No
Character at position 7: W
Substring from position 7 with length 5: World
Position of 'World' in the greeting: 7
Modified greeting: Hello, C++!
```

std::string 成员函数汇总表 下面是一个常见的 std::string 成员函数的汇总:


## 实例

输出结果:

```text
Length: 13
Is empty? No
First character: H
Character at position 7: W
Substring from position 7 with length 5: World
Position of 'World': 7
Modified string: Hello, C++!
Appended string: Hello, C++! How are you?
String after insert: Hello,  BeautifulC++! How are you?
String after erase: Hello, C++! How are you?
String after clear: Empty
C-style string: Hello, C++!
Comparison result: 0
First vowel at position: 1
Last vowel at position: 4
First non-vowel at position: 0
Last non-vowel at position: 10
```


## 复习重点

- 能说明 `C++ <string>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
