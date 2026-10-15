# C 语言数据结构与算法：C 语言环境搭建

- 来源：[C 语言环境搭建](https://www.runoob.com/c-dsa/c-dsa-env-setup.html)
- 分类：计算机基础
- 技术：C 语言数据结构与算法
- 笔记类型：练习笔记
- 章节序号：1218

## 本章内容

在开始学习数据结构与算法之前，需要先搭建一个可以顺利编译和运行 C 程序的开发环境。

也可以参考我们的 C 语言教程章节安装设置：https://www.runoob.com/cprogramming/c-environment-setup.html


## 编译器安装

本教程推荐使用 GCC（GNU Compiler Collection），它是跨平台、开源且广泛应用于生产环境的 C 语言编译器。


### Windows 系统

在 Windows 上，推荐通过 MinGW-w64 或 MSYS2 来获得 GCC 编译环境。

安装步骤：

- 访问 MinGW-w64 官网 下载安装程序
- 运行安装程序，选择架构为 x86_64，线程模型选 posix
- 安装完成后，将 MinGW-w64 的 bin 目录（如 C:\mingw64\bin）添加到系统环境变量 PATH 中
- 打开命令提示符（cmd），输入 gcc --version 验证安装是否成功


### macOS 系统

在 macOS 上，安装 Xcode 命令行工具即可获得 GCC（实际是 Clang 的封装，兼容 GCC 用法）。

打开终端，执行以下命令：

```text
$ xcode-select --install
```

系统会弹出安装提示，点击"安装"并等待完成。

安装完成后，验证编译器是否可用：

```text
$ gcc --version
Apple clang version 16.0.0 (clang-1600.0.26.4)
Target: arm64-apple-darwin25.5.0
Thread model: posix
```


### Linux 系统

大多数 Linux 发行版都可以通过包管理器一键安装 GCC。

Ubuntu/Debian 系统：

```text
$ sudo apt update
$ sudo apt install gcc build-essential
```

Fedora/CentOS 系统：

```text
$ sudo dnf install gcc gcc-c++
```

验证安装：

```text
$ gcc --version
gcc (Ubuntu 13.2.0-4ubuntu3) 13.2.0
```


## IDE 推荐

以下是几款适合初学者的 C 语言集成开发环境。

本教程的代码示例不依赖特定 IDE，使用任何一款都可以正常编译运行。

如果你不想在本地安装任何工具，也可以使用在线编译器（如 Compiler Explorer、OnlineGDB）快速验证代码。

对于初学者，本教程推荐 VS Code + MinGW-w64（Windows）或 VS Code + Xcode 命令行工具（macOS）的组合，轻量且功能完备。


## 第一个 C 程序

搭建好环境后，立即编写并运行经典的 "Hello, World!" 程序，确认一切配置正确。

创建一个新文件，命名为 hello.c，输入以下代码：


## 实例

代码结构说明（从上到下）：

保存文件后，在终端中使用以下命令编译并运行：

```text
# 编译：将 hello.c 编译为可执行文件 hello
$ gcc hello.c -o hello

# 运行，Windows 下为 hello.exe
$ ./hello
Hello, World! Welcome to RUNOOB DSA Tutorial!
```

如果终端中正确输出了上述文字，说明你的 C 语言开发环境已经配置成功。


## 编译命令详解

GCC 编译命令的基本格式为：

```text
gcc [选项] 源文件 -o 输出文件
```

常用编译选项：

本教程推荐日常使用的编译命令：

```text
$ gcc -Wall -g -std=c11 hello.c -o hello
```

这条命令会启用警告、生成调试信息、使用 C11 标准来编译你的程序。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C 语言环境搭建` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
