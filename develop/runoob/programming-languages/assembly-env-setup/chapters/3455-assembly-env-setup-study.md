# 汇编语言：汇编语言 - 环境搭建

- 来源：[汇编语言 - 环境搭建](https://www.runoob.com/assembly/assembly-env-setup.html)
- 分类：编程语言
- 技术：汇编语言
- 笔记类型：学习笔记
- 章节序号：3455

## 本章内容

本章将指导你在 Linux 系统上搭建 NASM 汇编开发环境，并完成你的第一个汇编程序。


## Linux 环境准备

如果你使用的是 Windows 系统，建议安装 WSL（Windows Subsystem for Linux） 或使用虚拟机来获得 Linux 环境。

macOS 用户可以在虚拟机中安装 Linux 或使用 Docker 容器。

本教程所有示例基于 Ubuntu/Debian 系统，其他发行版请自行调整包管理器命令。


## 安装 NASM 汇编器

在 Ubuntu/Debian 系统上，使用 apt 包管理器安装 NASM：

```text
$ sudo apt update
$ sudo apt install nasm
```

安装完成后，验证 NASM 是否安装成功：

```text
$ nasm -version
NASM version 2.16.01
```

如果你看到版本号输出，说明 NASM 已成功安装。


## 安装链接器

汇编器生成的是 目标文件（.o 文件），不能直接运行。

你需要链接器将目标文件转换为可执行文件。我们使用 GCC 自带的链接器：

```text
$ sudo apt install gcc
```

除此之外，你也可以直接使用 GNU 链接器 ld：

```text
$ ld --version
```

在本教程中，我们主要使用 gcc 来链接，因为它会自动处理一些底层细节，更适合初学者。


## 安装调试工具 GDB

GDB（GNU Debugger） 是 Linux 下最常用的调试器，可以单步执行程序、查看寄存器状态、检查内存内容。

```text
$ sudo apt install gdb
```

验证 GDB 安装：

```text
$ gdb --version
GNU gdb (Ubuntu 12.1-0ubuntu1) 12.1
```


## 第一个汇编程序：Hello, runoob

创建一个新文件 hello.asm，输入以下内容：


## 实例


## 编译和运行

整个编译运行流程如图所示：

使用以下命令编译和运行这个程序：

```text
$ nasm -f elf32 hello.asm -o hello.o    # 汇编：将 .asm 转为 .o 目标文件
$ ld -m elf_i386 hello.o -o hello       # 链接：将 .o 转为可执行文件
$ ./hello                               # 运行程序
Hello, runoob!
```

上面三条命令各自的作用：


## 使用 GCC 链接（推荐方式）

如果你的环境中的 ld 配置比较复杂，可以使用 gcc 来链接，它会自动处理 C 运行时等细节：

```text
$ nasm -f elf32 hello.asm -o hello.o
$ gcc -m32 hello.o -o hello -nostartfiles
$ ./hello
Hello, runoob!
```

-nostartfiles 选项告诉 GCC 不要添加默认的启动代码，因为我们自己定义了 _start 入口点。


## 代码结构解析

让我们逐段理解上面的程序：

int 0x80 是 Linux 32 位系统调用指令。它触发一个软件中断，让内核执行我们通过 eax 指定的系统调用。这是用户程序和操作系统内核之间的桥梁。


## 使用 GDB 调试

编译时添加调试信息，然后用 GDB 逐步执行：

```text
$ nasm -f elf32 -g hello.asm -o hello.o       # -g 添加调试信息
$ ld -m elf_i386 hello.o -o hello
$ gdb ./hello
(gdb) break _start                             # 在 _start 处设置断点
(gdb) run                                      # 运行程序
(gdb) stepi                                    # 单步执行一条指令
(gdb) info registers                           # 查看所有寄存器
(gdb) x/s msg                                  # 查看 msg 字符串内容
(gdb) quit                                     # 退出 GDB
```


## 常见问题

如果你在 64 位系统上编译 32 位汇编，需要安装 32 位兼容库：sudo apt install gcc-multilib

如果 ld 链接时报错 "cannot find entry symbol _start"，检查你的代码中是否写对了 global _start 以及标签名是否完全一致（注意下划线）。


## 复习重点

- 能说明 `汇编语言 - 环境搭建` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
