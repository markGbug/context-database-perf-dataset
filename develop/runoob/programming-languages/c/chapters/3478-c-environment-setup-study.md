# C：C 环境设置

- 来源：[C 环境设置](https://www.runoob.com/cprogramming/c-environment-setup.html)
- 分类：编程语言
- 技术：C
- 笔记类型：学习笔记
- 章节序号：3478

## 本章内容

如果您想要设置 C 语言环境，您需要确保电脑上有以下两款可用的软件，文本编辑器和 C 编译器。


## 文本编辑器

通过编辑器创建的文件通常称为源文件，源文件包含程序源代码。

C 程序的源文件通常使用扩展名 .c。

在开始编程之前，请确保您有一个文本编辑器，且有足够的经验来编写一个计算机程序，然后把它保存在一个文件中，编译并执行它。

- Visual Studio Code：虽然它是一个通用的文本编辑器，但它有很多插件支持 C/C++ 开发，使其成为一个流行的选择，通过安装 C/C++ 插件和调整设置，你可以使其成为一个很好的 C 语言开发环境。安装教程：https://www.runoob.com/w3cnote/vscode-tutorial.html 下载地址：https://code.visualstudio.com/
- Sublime Text：Sublime Text 是一个轻量级、快速和高度可定制的文本编辑器，有很多插件支持 C 语言的开发。它具有强大的代码编辑功能和快捷键，使得编码更加高效。 下载地址：https://www.sublimetext.com/
- Atom：Atom 是一个开源的文本编辑器，由 GitHub 开发，它有很多插件和主题，可以定制为一个适合 C 语言开发的环境。 下载地址：https://atom-editor.cc/
- Vim 和 Emacs：这两个是传统的文本编辑器，它们有着强大的编辑功能和高度的可定制性，对于熟练的用户来说非常强大，有很多插件和配置可以支持C语言的开发。
- Eclipse：Eclipse 是另一个功能强大的集成开发环境，虽然它最初是为 Java 开发设计的，但通过安装 C/C++ 插件，可以使其支持 C 语言开发。


## C 编译器

写在源文件中的源代码是人类可读的源。它需要"编译"，转为机器语言，这样 CPU 可以按给定指令执行程序。

C 语言编译器用于把源代码编译成最终的可执行程序。这里假设您已经对编程语言编译器有基本的了解了。

最常用的免费可用的编译器是 GNU 的 C/C++ 编译器，如果您使用的是 HP 或 Solaris，则可以使用各自操作系统上的编译器。

以下部分将指导您如何在不同的操作系统上安装 GNU 的 C/C++ 编译器。这里同时提到 C/C++，主要是因为 GNU 的 gcc 编译器适合于 C 和 C++ 编程语言。


## UNIX/Linux 上的安装

如果您使用的是 Linux 或 UNIX，请在命令行使用下面的命令来检查您的系统上是否安装了 GCC：

```text
$ gcc -v
```

如果您的计算机上已经安装了 GNU 编译器，则会显示如下消息：

```text
Using built-in specs.
Target: i386-redhat-linux
Configured with: ../configure --prefix=/usr .......
Thread model: posix
gcc version 4.1.2 20080704 (Red Hat 4.1.2-46)
```

如果未安装 GCC，那么请按照 http://gcc.gnu.org/install/ 上的详细说明安装 GCC。

本教程是基于 Linux 编写的，所有给定的实例都已在 Cent OS Linux 系统上编译过。


## Mac OS 上的安装

如果您使用的是 Mac OS X，最快捷的获取 GCC 的方法是从苹果的网站上下载 Xcode 开发环境，并按照安装说明进行安装。一旦安装上 Xcode，您就能使用 GNU 编译器。

Xcode 目前可从 developer.apple.com/technologies/tools/ 上下载。


## Windows 上的安装


### Cygwin

Cygwin 是一个在 Windows 操作系统上模拟 Unix/Linux 环境的软件包，它允许用户在 Windows 上使用类 Unix 工具和应用程序。

Cygwin 通过提供一组 DLL（动态链接库），这些 DLL 充当 Unix 系统调用层和 Windows 内核之间的桥梁，使得 Unix 程序能够在 Windows 系统上运行。

Cygwin 官网：https://www.cygwin.com/。

在官网下载安装包：

下载完成后，双击下载的文件：

接下来可以一直点击下一步(Next):

这里我们可以添加网易开源镜像阿里云镜像 https://mirrors.aliyun.com/cygwin/：

安装完成后，就会在桌面生成一个图标：

双击图标，进入命令行界面，输入 cygcheck -c cygwin命令可以查看当前的 cygwin 的版本信息：

接下来我们安装 gcc/g++ 的编译环境，在命令行进入 setup-x86_64.exe 目录下，执行：

```text
setup-x86_64.exe -q -P wget -P gcc-g++ -P make -P diffutils -P libmpfr-devel -P libgmp-devel -P libmpc-devel
```

安装完成后，进入 Cygwin64 终端， 输入 gcc --version 命令就可以查看版本信息了。


### MinGW-w64

为了在 Windows 上安装 GCC，您需要安装 MinGW-w64。

MinGW-w64 是一个开源项目，它为 Windows 系统提供了一个完整的 GCC 工具链，支持编译生成 32 位和 64 位的 Windows 应用程序。

访问 MinGW-w64 的主页 mingw-w64.org，进入 MinGW 下载页面 https://www.mingw-w64.org/downloads/，下载最新版本的 MinGW-w64 安装程序。

MinGW-w64 的下载详情页面包含了很多 MinGW-w64 及特定工具的整合包：

我们只安装 MinGW-w64 ，所以只需下载 MinGW-w64 即可，点击红框中的"SourceForge"超链接，就会进入 SourceForge 中的 MinGW-w64 下载页面。

在 SourceForge 上下载 MinGW-w64 ：https://sourceforge.net/projects/mingw-w64/files/

Github 上也有编译好的二进制包：https://github.com/niXman/mingw-builds-binaries/releases

可以下载指定系统的安装程序：

- 32 位系统：installer.exe
- 64 位系统：installer.exe

这种安装，会碰到网络连接错误问题，所以我们可以直接下载 sjlj （稳定的，64 位和 32 位都支持）：

- 下载 32 位 sjlj
- 下载 64 位 sjlj

下载完成后，解压，在 bin 目录里面就可以找到 g++.exe 或者 gcc.exe：

当安装 MinGW 时，您至少要安装 gcc-core、gcc-g++、binutils 和 MinGW runtime，但是一般情况下都会安装更多其他的项。

添加您安装的 MinGW 的 bin 子目录到您的 PATH 环境变量中，这样您就可以在命令行中通过简单的名称来指定这些工具。

当完成安装时，您可以从 Windows 命令行上运行 gcc、g++、ar、ranlib、dlltool 和其他一些 GNU 工具。


## 复习重点

- 能说明 `C 环境设置` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
