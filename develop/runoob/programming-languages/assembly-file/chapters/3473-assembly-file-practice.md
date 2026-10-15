# 汇编语言：汇编语言 - 文件管理

- 来源：[汇编语言 - 文件管理](https://www.runoob.com/assembly/assembly-file.html)
- 分类：编程语言
- 技术：汇编语言
- 笔记类型：练习笔记
- 章节序号：3473

## 本章内容

文件管理是程序与外部存储交互的基础。

通过系统调用，汇编程序可以打开、读取、写入和关闭文件，与高级语言一样灵活地处理文件 IO。


## 文件操作流程总览

文件操作遵循打开→读写→关闭的基本流程，以及三个标准文件描述符：


## 文件操作相关的系统调用


## 文件打开标志

多个标志用 OR 组合，例如 O_WRONLY | O_CREAT | O_TRUNC = 1 | 64 | 512 = 577


## 创建并写入文件


## 实例

运行结果：

```text
$ nasm -f elf32 file_write.asm -o file_write.o
$ ld -m elf_i386 file_write.o -o file_write
$ ./file_write
File created successfully!
$ cat runoob_output.txt
Hello, RUNOOB!
```


## 读取文件内容


## 实例

运行结果：

```text
$ nasm -f elf32 file_read.asm -o file_read.o
$ ld -m elf_i386 file_read.o -o file_read
$ ./file_read
File content:
Hello, RUNOOB!
```


## 追加写入文件


## 实例


## 复制文件

一个综合示例：将一个文件的内容复制到另一个文件：


## 实例

文件操作前后务必检查系统调用的返回值（在 EAX 中）。负值表示错误（如 -2 是 ENOENT 文件不存在，-13 是 EACCES 权限不足），忽略错误返回值是文件操作 bug 的最大来源。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `汇编语言 - 文件管理` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
