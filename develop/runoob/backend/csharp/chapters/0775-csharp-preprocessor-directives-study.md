# C#：C# 预处理器指令

- 来源：[C# 预处理器指令](https://www.runoob.com/csharp/csharp-preprocessor-directives.html)
- 分类：后端开发
- 技术：C#
- 笔记类型：学习笔记
- 章节序号：0775

## 本章内容

预处理器指令（Preprocessor Directives）指导编译器在实际编译开始之前对信息进行预处理。

通过这些指令，可以控制编译器如何编译文件或编译哪些部分。常见的预处理器指令包括条件编译、宏定义等。

所有的预处理器指令都是以 # 开始，且在一行上，只有空白字符可以出现在预处理器指令之前。

预处理器指令不是语句，所以它们不以分号 ; 结束。

C# 编译器没有一个单独的预处理器，但是，指令被处理时就像是有一个单独的预处理器一样。在 C# 中，预处理器指令用于在条件编译中起作用。与 C 和 C++ 不同的是，它们不是用来创建宏。一个预处理器指令必须是该行上的唯一指令。


## C# 预处理器指令列表

下表列出了 C# 中可用的预处理器指令：


## 实例


## #define 和 #undef 预处理器

#define 用于定义符号（通常用于条件编译），#undef 用于取消定义符号。

```text
#define DEBUG

#undef RELEASE
```

#define 允许您定义一个符号，这样，通过使用符号作为传递给 #if 指令的表达式，表达式将返回 true。它的语法如下：

```text
#define symbol
```

下面的程序说明了这点：


## 实例

当上面的代码被编译和执行时，它会产生下列结果：

```text
PI is defined
```


## 条件指令：#if, #elif, #else 和 #endif

您可以使用 #if 指令来创建一个条件指令。

条件指令用于测试符号是否为真。如果为真，编译器会执行 #if 和下一个指令之间的代码。

条件指令的语法：

```text
#if symbol [operator symbol]...
```

其中，symbol 是要测试的符号名称。您也可以使用 true 和 false，或在符号前放置否定运算符。

常见运算符有：

- == (等于)
- != (不等于)
- && (与)
- || (或)

您也可以用括号把符号和运算符进行分组。条件指令用于在调试版本或编译指定配置时编译代码。一个以 #if 指令开始的条件指令，必须显示地以一个 #endif 指令终止。

```text
#define DEBUG

#if DEBUG
    Console.WriteLine("Debug mode");
#elif RELEASE
    Console.WriteLine("Release mode");
#else
    Console.WriteLine("Other mode");
#endif
```

下面的程序演示了条件指令的用法：


## 实例

当上面的代码被编译和执行时，它会产生下列结果：

```text
DEBUG and VC_V10 are defined
```


## #warning 和 #error

#warning 用于生成编译器警告，#error 用于生成编译器错误。

```text
#warning This is a warning message
#error This is an error message
```


## #region 和 #endregion

用于代码折叠，使代码更加可读。

```text
#region MyRegion
    // Your code here
#endregion
```


## #line

用于更改文件行号和文件名的编译器输出。

```text
#line 100 "MyFile.cs"
    // The next line will be reported as line 100 in MyFile.cs
    Console.WriteLine("This is line 100");
#line default
    // Line numbering returns to normal
```


## #pragma

用于向编译器发送特殊指令。最常见的用法是禁用特定的警告。

```java
#pragma warning disable 414
    private int unusedVariable;
#pragma warning restore 414
```


## 使用预处理器指令的注意事项

- 提高代码可读性：使用#region可以帮助分隔代码块，提高代码的组织性。
- 条件编译：通过#if等指令可以在开发和生产环境中编译不同的代码，方便调试和发布。
- 警告和错误：通过#warning和#error可以在编译时提示开发人员注意特定问题。

通过正确使用这些预处理器指令，可以更好地控制代码的编译过程，提高代码的灵活性和可维护性。


## 复习重点

- 能说明 `C# 预处理器指令` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
