# C：C 预处理器

- 来源：[C 预处理器](https://www.runoob.com/cprogramming/c-preprocessors.html)
- 分类：编程语言
- 技术：C
- 笔记类型：练习笔记
- 章节序号：3502

## 本章内容

C 预处理器(CPP)是编译过程中的独立阶段，在实际编译前对源代码进行文本处理。主要功能包括：

- 宏展开
- 文件包含
- 条件编译
- 特殊指令处理

C 预处理器不是编译器的组成部分，但是它是编译过程中一个单独的步骤。

简言之，C 预处理器只不过是一个文本替换工具而已，它们会指示编译器在实际编译之前完成所需的预处理。

我们将把 C 预处理器（C Preprocessor）简写为 CPP。

所有的预处理器命令都是以井号 # 开头。它必须是第一个非空字符，为了增强可读性，预处理器指令应从第一列开始。

下面列出了所有重要的预处理器指令：


## 预处理器实例

分析下面的实例来理解不同的指令。

```text
#define MAX_ARRAY_LENGTH 20
```

这个指令告诉 CPP 把所有的 MAX_ARRAY_LENGTH 定义为 20。使用 #define 定义常量来增强可读性。

```html
#include <stdio.h>
#include "myheader.h"
```

这些指令告诉 CPP 从系统库中获取 stdio.h，并添加文本到当前的源文件中。下一行告诉 CPP 从本地目录中获取 myheader.h，并添加内容到当前的源文件中。

```text
#undef  FILE_SIZE
#define FILE_SIZE 42
```

这个指令告诉 CPP 取消已定义的 FILE_SIZE，并定义它为 42。

```text
#ifndef MESSAGE
   #define MESSAGE "You wish!"
#endif
```

这个指令告诉 CPP 只有当 MESSAGE 未定义时，才定义 MESSAGE。

```text
#ifdef DEBUG
   /* Your debugging statements here */
#endif
```

这个指令告诉 CPP 如果定义了 DEBUG，则执行处理语句。在编译时，如果您向 gcc 编译器传递了 -DDEBUG 开关量，这个指令就非常有用。它定义了 DEBUG，您可以在编译期间随时开启或关闭调试。


## 实例


### 最佳实践建议

- 宏命名： 使用全大写字母和下划线命名宏 示例：#define MAX_SIZE 100
- 函数式宏注意事项： 每个参数和整个表达式都要用括号括起来 避免使用有副作用的参数（如SQUARE(x++)）
- 头文件保护： #ifndef MY_HEADER_H #define MY_HEADER_H /* 头文件内容 */ #endif
- 条件编译调试： #ifdef DEBUG #define DEBUG_PRINT(fmt, ...) printf(fmt, ##__VA_ARGS__) #else #define DEBUG_PRINT(fmt, ...) #endif
- 跨平台开发： #if defined(_WIN32) // Windows特定代码 #elif defined(__linux__) // Linux特定代码 #elif defined(__APPLE__) // macOS特定代码 #endif


## 预定义宏

ANSI C 定义了许多宏。在编程中您可以使用这些宏，但是不能直接修改这些预定义的宏。

让我们来尝试下面的实例：


## 实例

```java
#include <stdio.h>

/*
 * 预定义宏演示程序
 * 展示ANSI C标准中常用的预定义宏及其用途
 */
int main() {
    // 打印当前源文件名（字符串常量）
    printf("当前文件: %s\n", __FILE__);

    // 打印编译日期（"MMM DD YYYY"格式）
    printf("编译日期: %s\n", __DATE__);

    // 打印编译时间（"HH:MM:SS"格式）
    printf("编译时间: %s\n", __TIME__);

    // 打印当前行号（十进制整数）
    printf("当前行号: %d\n", __LINE__);

    // 检查是否符合ANSI/ISO标准（1表示符合）
    printf("ANSI标准: %d\n", __STDC__);

    // 实用示例：调试信息输出
    printf("\n[调试信息] %s (第%d行) 编译于 %s %s\n",
           __FILE__, __LINE__, __DATE__, __TIME__);

    return 0;
}
```

当上面的代码（在文件 test.c 中）被编译和执行时，它会产生下列结果：

```text
当前文件: predef_macros.c
编译日期: Jul 5 2023
编译时间: 14:30:45
当前行号: 13
ANSI标准: 1

[调试信息] predef_macros.c (第16行) 编译于 Jul 5 2023 14:30:45
```


## 预处理器运算符

C 预处理器提供了下列的运算符来帮助您创建宏：


### 宏延续运算符（\）

一个宏通常写在一个单行上。但是如果宏太长，一个单行容纳不下，则使用宏延续运算符（\）。例如：

```java
#define  message_for(a, b)  \
    printf(#a " and " #b ": We love you!\n")
```

在宏定义中，当需要把一个宏的参数转换为字符串常量时，则使用字符串常量化运算符（#）。在宏中使用的该运算符有一个特定的参数或参数列表。例如：


## 实例

```java
#include <stdio.h>

#define  message_for(a, b)  \
    printf(#a " and " #b ": We love you!\n")

int main(void)
{
   message_for(Carole, Debra);
   return 0;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```text
Carole and Debra: We love you!
```


### 标记粘贴运算符（##）

宏定义内的标记粘贴运算符（##）会合并两个参数。它允许在宏定义中两个独立的标记被合并为一个标记。例如：


## 实例

```java
#include <stdio.h>

#define tokenpaster(n) printf ("token" #n " = %d", token##n)

int main(void)
{
   int token34 = 40;

   tokenpaster(34);
   return 0;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```text
token34 = 40
```

这是怎么发生的，因为这个实例会从编译器产生下列的实际输出：

```text
printf ("token34 = %d", token34);
```

这个实例演示了 token##n 会连接到 token34 中，在这里，我们使用了字符串常量化运算符（#）和标记粘贴运算符（##）。


### defined() 运算符

预处理器 defined 运算符是用在常量表达式中的，用来确定一个标识符是否已经使用 #define 定义过。如果指定的标识符已定义，则值为真（非零）。如果指定的标识符未定义，则值为假（零）。下面的实例演示了 defined() 运算符的用法：


## 实例

```java
#include <stdio.h>

#if !defined (MESSAGE)
   #define MESSAGE "You wish!"
#endif

int main(void)
{
   printf("Here is the message: %s\n", MESSAGE);
   return 0;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```text
Here is the message: You wish!
```


## 参数化的宏

CPP 一个强大的功能是可以使用参数化的宏来模拟函数。例如，下面的代码是计算一个数的平方：

```java
int square(int x) {
   return x * x;
}
```

我们可以使用宏重写上面的代码，如下：

```text
#define square(x) ((x) * (x))
```

在使用带有参数的宏之前，必须使用 #define 指令定义。参数列表是括在圆括号内，且必须紧跟在宏名称的后边。宏名称和左圆括号之间不允许有空格。例如：


## 实例

```java
#include <stdio.h>

#define MAX(x,y) ((x) > (y) ? (x) : (y))

int main(void)
{
   printf("Max between 20 and 10 is %d\n", MAX(10, 20));
   return 0;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```text
Max between 20 and 10 is 20
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C 预处理器` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
