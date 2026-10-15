# C：C 标准库 - <stddef.h>

- 来源：[C 标准库 - <stddef.h>](https://www.runoob.com/cprogramming/c-standard-library-stddef-h.html)
- 分类：编程语言
- 技术：C
- 笔记类型：练习笔记
- 章节序号：3526

## 本章内容

## 简介

stddef .h 头文件定义了各种变量类型和宏，这些定义和宏主要用于内存管理、对象大小、和指针算术等方面。


## 库变量

下面是头文件 stddef.h 中定义的变量类型：

ptrdiff_t 是一种有符号整数类型，用于表示两个指针之间的差值。其定义同样依赖于实现，通常是 int 或 long。

```text
ptrdiff_t diff = ptr2 - ptr1; // 计算两个指针之间的差值
```

这是无符号整数类型，它是 sizeof 关键字的结果，通常用来表示对象的大小或数组的索引。其定义依赖于实现，通常是 unsigned int 或 unsigned long。

```java
size_t size = sizeof(int); // 获取 int 类型的大小
```

这是一个宽字符常量大小的整数类型，用于表示多字节字符。其大小和表示方式依赖于具体实现。

```text
wchar_t wideChar = L'A'; // 宽字符常量
```


## 库宏

下面是头文件 stddef.h 中定义的宏：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C 标准库 - <stddef.h>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
