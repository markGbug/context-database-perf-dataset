# C：C 字符串

- 来源：[C 字符串](https://www.runoob.com/cprogramming/c-strings.html)
- 分类：编程语言
- 技术：C
- 笔记类型：学习笔记
- 章节序号：3495

## 本章内容

在 C 语言中，字符串实际上是使用空字符 \0 结尾的一维字符数组。因此，\0 是用于标记字符串的结束。

空字符（Null character）又称结束符，缩写 NUL，是一个数值为 0 的控制字符，\0 是转义字符，意思是告诉编译器，这不是字符 0，而是空字符。

下面的声明和初始化创建了一个 RUNOOB 字符串。由于在数组的末尾存储了空字符 \0，所以字符数组的大小比单词 RUNOOB 的字符数多一个。

```text
char site[7] = {'R', 'U', 'N', 'O', 'O', 'B', '\0'};
```

依据数组初始化规则，您可以把上面的语句写成以下语句：

```text
char site[] = "RUNOOB";
```

以下是 C/C++ 中定义的字符串的内存表示：

其实，您不需要把 null 字符放在字符串常量的末尾。C 编译器会在初始化数组时，自动把 \0 放在字符串的末尾。让我们尝试输出上面的字符串：


## 实例

```java
#include <stdio.h>

int main ()
{
   char site[7] = {'R', 'U', 'N', 'O', 'O', 'B', '\0'};

   printf("菜鸟教程: %s\n", site );

   return 0;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```text
菜鸟教程: RUNOOB
```

C 中有大量操作字符串的函数：

下面的实例使用了上述的一些函数：


## 实例

```java
#include <stdio.h>
#include <string.h>

int main ()
{
   char str1[14] = "runoob";
   char str2[14] = "google";
   char str3[14];
   int  len ;

   /* 复制 str1 到 str3 */
   strcpy(str3, str1);
   printf("strcpy( str3, str1) :  %s\n", str3 );

   /* 连接 str1 和 str2 */
   strcat( str1, str2);
   printf("strcat( str1, str2):   %s\n", str1 );

   /* 连接后，str1 的总长度 */
   len = strlen(str1);
   printf("strlen(str1) :  %d\n", len );

   return 0;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```text
strcpy( str3, str1) :  runoob
strcat( str1, str2):   runoobgoogle
strlen(str1) :  12
```

您可以在 C 标准库中找到更多字符串相关的函数。


## 复习重点

- 能说明 `C 字符串` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
