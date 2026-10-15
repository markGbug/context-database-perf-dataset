# C++：C++ 环境设置

- 来源：[C++ 环境设置](https://www.runoob.com/cplusplus/cpp-environment-setup.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：练习笔记
- 章节序号：3539

## 本章内容

如果您想要设置 C++ 语言环境，您需要确保电脑上有以下两款可用的软件，文本编辑器和 C++ 编译器。


## 文本编辑器

通过编辑器创建的文件通常称为源文件，源文件包含程序源代码。

C++ 程序的源文件通常使用扩展名 .cpp、.cp 或 .c。

在开始编程之前，请确保您有一个文本编辑器，且有足够的经验来编写一个计算机程序，然后把它保存在一个文件中，编译并执行它。

- Visual Studio Code：虽然它是一个通用的文本编辑器，但它有很多插件支持 C/C++ 开发，使其成为一个流行的选择，通过安装 C/C++ 插件和调整设置，你可以使其成为一个很好的 C 语言开发环境。安装教程：https://www.runoob.com/w3cnote/vscode-tutorial.html 下载地址：https://code.visualstudio.com/
- Visual Studio： 面向 .NET 和 C++ 开发人员的综合性 Windows 版 IDE，可用于构建 Web、云、桌面、移动应用、服务和游戏。 下载地址：https://visualstudio.microsoft.com/zh-hans/downloads/。
- Vim 和 Emacs：这两个是传统的文本编辑器，它们有着强大的编辑功能和高度的可定制性，对于熟练的用户来说非常强大，有很多插件和配置可以支持C语言的开发。
- Eclipse：Eclipse 是另一个功能强大的集成开发环境，虽然它最初是为 Java 开发设计的，但通过安装 C/C++ 插件，可以使其支持 C 语言开发。


### 更多相关工具


## C++ 编译器

写在源文件中的源代码是人类可读的源。它需要"编译"，转为机器语言，这样 CPU 可以按给定指令执行程序。

C++ 编译器用于把源代码编译成最终的可执行程序。

大多数的 C++ 编译器并不在乎源文件的扩展名，但是如果您未指定扩展名，则默认使用 .cpp。

最常用的免费可用的编译器是 GNU 的 C/C++ 编译器，如果您使用的是 HP 或 Solaris，则可以使用各自操作系统上的编译器。

以下部分将指导您如何在不同的操作系统上安装 GNU 的 C/C++ 编译器。这里同时提到 C/C++，主要是因为 GNU 的 gcc 编译器适合于 C 和 C++ 编程语言。


## UNIX/Linux 上的安装

如果您使用的是 Linux 或 UNIX，请在命令行使用下面的命令来检查您的系统上是否安装了 GCC：

```text
$ g++ -v
```

如果您的计算机上已经安装了 GNU 编译器，则会显示如下消息：

```text
Using built-in specs.
Target: i386-redhat-linux
Configured with: ../configure --prefix=/usr .......
Thread model: posix
gcc version 4.1.2 20080704 (Red Hat 4.1.2-46)
```

如果未安装 GCC，那么请按照 https://gcc.gnu.org/install/ 上的详细说明安装 GCC。


## Mac OS X 上的安装

如果您使用的是 Mac OS X，最快捷的获取 GCC 的方法是从苹果的网站上下载 Xcode 开发环境，并按照安装说明进行安装。一旦安装上 Xcode，您就能使用 GNU 编译器。

Xcode 目前可从 https://developer.apple.com/download 上下载，需要使用 apple ID 登录 。


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

也可以在 Github 上下载：https://github.com/niXman/mingw-builds-binaries/releases

MinGW-w64 的下载详情页面包含了很多 MinGW-w64 及特定工具的整合包：

我们只安装 MinGW-w64 ，所以只需下载 MinGW-w64 即可，点击红框中的"SourceForge"超链接，就会进入 SourceForge 中的 MinGW-w64 下载页面。

在 SourceForge 上下载 MinGW-w64 ：https://sourceforge.net/projects/mingw-w64/files/

页面往下滑，下载安装程序：

这种安装，会碰到网络连接错误问题，所以我们可以直接下载 sjlj （稳定的，64 位和 32 位都支持）：

下载完成后，解压，在 bin 目录里面就可以找到 g++.exe 或者 gcc.exe：

当安装 MinGW 时，您至少要安装 gcc-core、gcc-g++、binutils 和 MinGW runtime，但是一般情况下都会安装更多其他的项。

添加您安装的 MinGW 的 bin 子目录到您的 PATH 环境变量中，这样您就可以在命令行中通过简单的名称来指定这些工具。

当完成安装时，您可以从 Windows 命令行上运行 gcc、g++、ar、ranlib、dlltool 和其他一些 GNU 工具。


## 使用 Visual Studio (Graphical Interface) 编译

1、下载及安装 Visual Studio 下载。

2、打开 Visual Studio Community

3、点击 File -> New -> Project

4、左侧列表选择 Templates -> Visual C++ -> Win32 Console Application，并设置项目名为 MyFirstProgram。

5、点击 OK。

6、在以下窗口中点击 Next

7、在弹出的窗口中选择 Empty project 选项后，点击 Finish 按钮：

8、右击文件夹 Source File 并点击 Add --> New Item... :

9、选择 C++ File 然后设置文件名为 main.cpp，然后点击 Add：

10、拷贝以下代码到 main.cpp 中：

```java
#include <iostream>

int main()
{
    std::cout << "Hello World!\n";
    return 0;
}
```

界面如下所示：

11、点击菜单上的 Debug -> Start Without Debugging (或按下 ctrl + F5) :

12、完成以上操作后，你可以看到以下输出：


## g++ 应用说明

程序 g++ 是将 gcc 默认语言设为 C++ 的一个特殊的版本，链接时它自动使用 C++ 标准库而不用 C 标准库。通过遵循源码的命名规范并指定对应库的名字，用 gcc 来编译链接 C++ 程序是可行的，如下例所示：

```text
$ gcc main.cpp -lstdc++ -o main
```

下面是一个保存在文件 helloworld.cpp 中一个简单的 C++ 程序的代码：

```java
#include <iostream>
using namespace std;
int main()
{
    cout << "Hello, world!" << endl;
    return 0;
}
```

最简单的编译方式：

```text
$ g++ helloworld.cpp
```

由于命令行中未指定可执行程序的文件名，编译器采用默认的 a.out。程序可以这样来运行：

```text
$ ./a.out
Hello, world!
```

通常我们使用 -o 选项指定可执行程序的文件名，以下实例生成一个 helloworld 的可执行文件：

```text
$ g++ helloworld.cpp -o helloworld
```

执行 helloworld:

```text
$ ./helloworld
Hello, world!
```

如果是多个 C++ 代码文件，如 runoob1.cpp、runoob2.cpp，编译命令如下：

```text
$ g++ runoob1.cpp runoob2.cpp -o runoob
```

生成一个 runoob 可执行文件。

g++ 有些系统默认是使用 C++98，我们可以指定使用 C++11 来编译 main.cpp 文件：

```text
g++ -g -Wall -std=c++11 main.cpp
```


### g++ 常用命令选项


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C++ 环境设置` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
