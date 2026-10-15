# C++：C++ 文件输入输出库 - <fstream>

- 来源：[C++ <fstream>](https://www.runoob.com/cplusplus/cpp-libs-fstream.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：练习笔记
- 章节序号：3585

## 本章内容

在 C++ 中， <fstream> 是标准库中用于文件输入输出操作的类。它提供了一种方便的方式来读写文件。

fstream是iostream库的一部分，支持文本和二进制文件的读写。

fstream类是iostream库中的一个类，它继承自istream和ostream类，这意味着它既可以用于输入也可以用于输出。


### 语法

fstream 的基本语法如下：

其中filename 是文件的名称，mode 是打开文件的模式，常见的模式有：

- std::ios::in：以输入模式打开文件。
- std::ios::out：以输出模式打开文件。
- std::ios::app：以追加模式打开文件。
- std::ios::ate：打开文件并定位到文件末尾。
- std::ios::trunc：打开文件并截断文件，即清空文件内容。


### 实例

写入文本文件:


## 实例

在当前目录下创建一个名为example.txt的文件，文件内容为：

```text
Hello, World!
```

读取文本文件


## 实例

如果 example.txt 文件包含以下内容：

```text
Hello, World!
This is a test file.
```

则程序将输出：

```text
Hello, World!
This is a test file.
```

追加到文件:


## 实例

example.txt 文件原本包含以下内容：

```text
Hello, World!
This is a test file.
```

执行上述程序后，文件内容将变为：

```text
Hello, World!
This is a test file.
Appending this line to the file.
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C++ <fstream>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
