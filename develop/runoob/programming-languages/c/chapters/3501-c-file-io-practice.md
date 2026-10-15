# C：C 文件读写

- 来源：[C 文件读写](https://www.runoob.com/cprogramming/c-file-io.html)
- 分类：编程语言
- 技术：C
- 笔记类型：练习笔记
- 章节序号：3501

## 本章内容

上一章我们讲解了 C 语言处理的标准输入和输出设备。本章我们将介绍 C 程序员如何创建、打开、关闭文本文件或二进制文件。

一个文件，无论它是文本文件还是二进制文件，都是代表了一系列的字节。C 语言不仅提供了访问顶层的函数，也提供了底层（OS）调用来处理存储设备上的文件。本章将讲解文件管理的重要调用。


## 打开文件

您可以使用 fopen( ) 函数来创建一个新的文件或者打开一个已有的文件，这个调用会初始化类型 FILE 的一个对象，类型 FILE 包含了所有用来控制流的必要的信息。下面是这个函数调用的原型：

```javascript
FILE *fopen( const char *filename, const char *mode );
```

在这里，filename 是字符串，用来命名文件，访问模式 mode 的值可以是下列值中的一个：

如果处理的是二进制文件，则需使用下面的访问模式来取代上面的访问模式：

```text
"rb", "wb", "ab", "rb+", "r+b", "wb+", "w+b", "ab+", "a+b"
```


## 关闭文件

为了关闭文件，请使用 fclose( ) 函数。函数的原型如下：

```java
 int fclose( FILE *fp );
```

如果成功关闭文件，fclose( ) 函数返回零，如果关闭文件时发生错误，函数返回 EOF。这个函数实际上，会清空缓冲区中的数据，关闭文件，并释放用于该文件的所有内存。EOF 是一个定义在头文件 stdio.h 中的常量。

C 标准库提供了各种函数来按字符或者以固定长度字符串的形式读写文件。


## 写入文件

下面是把字符写入到流中的最简单的函数：

```java
int fputc( int c, FILE *fp );
```

函数 fputc() 把参数 c 的字符值写入到 fp 所指向的输出流中。如果写入成功，它会返回写入的字符，如果发生错误，则会返回 EOF。您可以使用下面的函数来把一个以 null 结尾的字符串写入到流中：

```java
int fputs( const char *s, FILE *fp );
```

函数 fputs() 把字符串 s 写入到 fp 所指向的输出流中。如果写入成功，它会返回一个非负值，如果发生错误，则会返回 EOF。您也可以使用 int fprintf(FILE *fp,const char *format, ...) 函数把一个字符串写入到文件中。尝试下面的实例：

注意：请确保您有可用的 tmp 目录，如果不存在该目录，则需要在您的计算机上先创建该目录。

/tmp 一般是 Linux 系统上的临时目录，如果你在 Windows 系统上运行，则需要修改为本地环境中已存在的目录，例如: C:\tmp、D:\tmp等。


## 实例

```java
#include <stdio.h>

int main()
{
   FILE *fp = NULL;

   fp = fopen("/tmp/test.txt", "w+");
   fprintf(fp, "This is testing for fprintf...\n");
   fputs("This is testing for fputs...\n", fp);
   fclose(fp);
}
```

当上面的代码被编译和执行时，它会在 /tmp 目录中创建一个新的文件 test.txt，并使用两个不同的函数写入两行。接下来让我们来读取这个文件。


## 读取文件

下面是从文件读取单个字符的最简单的函数：

```java
int fgetc( FILE * fp );
```

fgetc() 函数从 fp 所指向的输入文件中读取一个字符。返回值是读取的字符，如果发生错误则返回 EOF。下面的函数允许您从流中读取一个字符串：

```java
char *fgets( char *buf, int n, FILE *fp );
```

函数 fgets() 从 fp 所指向的输入流中读取 n - 1 个字符。它会把读取的字符串复制到缓冲区 buf，并在最后追加一个 null 字符来终止字符串。

如果这个函数在读取最后一个字符之前就遇到一个换行符 '\n' 或文件的末尾 EOF，则只会返回读取到的字符，包括换行符。您也可以使用 int fscanf(FILE *fp, const char *format, ...) 函数来从文件中读取字符串，但是在遇到第一个空格和换行符时，它会停止读取。


## 实例

```java
#include <stdio.h>

int main()
{
   FILE *fp = NULL;
   char buff[255];

   fp = fopen("/tmp/test.txt", "r");
   fscanf(fp, "%s", buff);
   printf("1: %s\n", buff );

   fgets(buff, 255, (FILE*)fp);
   printf("2: %s\n", buff );

   fgets(buff, 255, (FILE*)fp);
   printf("3: %s\n", buff );
   fclose(fp);

}
```

当上面的代码被编译和执行时，它会读取上一部分创建的文件，产生下列结果：

```text
1: This
2: is testing for fprintf...

3: This is testing for fputs...
```

首先，fscanf() 方法只读取了 This，因为它在后边遇到了一个空格。其次，调用 fgets() 读取剩余的部分，直到行尾。最后，调用 fgets() 完整地读取第二行。


## 二进制 I/O 函数

下面两个函数用于二进制输入和输出：

```javascript
size_t fread(void *ptr, size_t size, size_t count, FILE *stream);
size_t fwrite(const void *ptr, size_t size, size_t count, FILE *stream);
```

fread 和 fwrite 是 C 语言标准库中用于二进制文件块读写的核心函数，它们直接操作内存数据块，避免了文本格式转换的开销，特别适合处理大文件和结构化数据的批量读写。


### 参数说明

四个参数在两个函数中含义一致，但数据流向相反：

实际操作的字节数为 size × count，返回值是成功读写的块数量而非字节数。若返回值小于 count，可能是文件结束（EOF）或读写错误导致，需要分别检查。


### 二进制模式与文本模式

使用 fread/fwrite 时必须用二进制模式打开文件，否则可能导致数据损坏。


### 为什么必须使用二进制模式

文本模式在 Windows 平台下会自动将换行符 \n 转换为 \r\n，这会破坏二进制数据的完整性。

Linux/macOS 下文本模式与二进制模式行为一致，但跨平台代码应显式使用 "b" 标志以保证可移植性。


## 实例

选择哪种函数取决于数据类型和需求场景：


### 数据读写流程图

下图展示了 fread 和 fwrite 在文件与内存之间的数据流向：


### 典型使用场景

这是 fread/fwrite 最常见的应用场景，可以将整个结构体作为一个数据块一次性读写。


## 实例

```text
学号: 101, 姓名: Alice, 成绩: 95.5
```

结构体中不能包含指针成员（如 char *name），因为 fwrite 只保存指针的地址值而非指向的字符串内容。读回时该地址已无效，导致悬空指针。正确做法是使用固定长度数组，如 char name[50]。

数组在内存中连续存放，可以一次性读写整个数组。


## 实例

```text
已写入 5 个整数到 array.bin
读取到的数据: 1 2 3 4 5
```

对于大文件，应使用循环分块读写，避免一次性加载全部内容到内存。


## 实例

```text
文件复制成功: runoob_input.bin -> runoob_output.bin
```

这个模式的关键在于 fread 返回实际读取的字节数，然后用 fwrite 只写入实际读取的字节数，避免了末尾多余数据的写入。


### 关键注意事项

调用 fread/fwrite 后必须检查返回值，区分正常结束与异常情况。


## 实例

```text
已到达文件末尾，实际读取 47 个元素
```

结构体在内存中的布局受编译器对齐策略影响，可能导致跨平台兼容性问题。

不同编译器或不同编译选项下，同一个结构体可能产生不同的内存布局。


## 实例

```text
默认对齐 Mixed 大小: 8 字节
紧凑对齐 PackedMixed 大小: 5 字节
```

推荐做法：跨平台或长期存储时，优先使用手动序列化（逐个成员读写），而非直接将结构体写入文件。这样可以完全避免对齐和字节序问题。

这是初学者最容易犯的错误之一。


## 实例

```text
演示完成，但 load 出来的 name 指针是无效的
```

C 标准库的 I/O 是带缓冲的，关键数据需要显式刷新以保证持久化。


## 实例

```text
使用 fflush 强制刷新到磁盘
fclose 也会自动刷新缓冲区
```

结合 fseek 和 ftell 可以实现文件的随机访问，按需读取指定位置的数据。


## 实例

```text
文件大小: 6000 字节
包含 100 条学生记录
第 6 条记录: id=106, name=RUNOOB
```


### 常见错误总结

下表汇总了使用 fread/fwrite 时最常遇到的问题及正确做法：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C 文件读写` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
