# C++：C++ 标准库 <cstdlib>

- 来源：[C++ <cstdlib>](https://www.runoob.com/cplusplus/cpp-libs-cstdlib.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：学习笔记
- 章节序号：3633

## 本章内容

<cstdlib> 是 C++ 标准库中的一个头文件，提供了各种通用工具函数，包括内存分配、进程控制、环境查询、排序和搜索、数学转换、伪随机数生成等。这些函数最初来自 C 标准库 <stdlib.h>，在 C++ 中进行了标准化和扩展。


### 语法

在 C++ 程序中，要使用 cstdlib 中的函数，需要先包含这个头文件：

```html
#include <cstdlib>
```


### 常用函数

cstdlib 中包含了许多有用的函数，以下是一些常用的函数及其简要说明：

- exit(int status): 终止程序执行，并返回一个状态码。
- system(const char* command): 执行一个命令行字符串。
- malloc(size_t size): 分配指定大小的内存。
- free(void* ptr): 释放之前分配的内存。
- atoi(const char* str): 将字符串转换为整数。
- atof(const char* str): 将字符串转换为浮点数。
- rand(): 生成一个随机数。
- srand(unsigned int seed): 设置随机数生成器的种子。


### 实例

以下是一些使用 cstdlib 中函数的实例：


### 实例 1：使用 exit 函数


## 实例

输出结果：

```text
This program will exit now.
```


### 实例 2：使用 system 函数


## 实例

输出结果：

```text
Executing a system command: dir
```

然后显示当前目录的文件和文件夹列表。


### 实例 3：使用 malloc 和 free 函数


## 实例

输出结果：

```text
Element 0: 0
Element 1: 1
Element 2: 4
...
Element 9: 81
```


### 实例 4：使用 atoi 和 atof 函数


## 实例

输出结果：

```text
Integer: 123
Float: 456.78
```


### 实例 5：使用 rand 和 srand 函数


## 实例

输出结果：

```text
53 22 62 68 62
```


## 复习重点

- 能说明 `C++ <cstdlib>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
