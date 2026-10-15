# C#：C# 开发环境

- 来源：[C# 开发环境](https://www.runoob.com/csharp/csharp-environment-setup.html)
- 分类：后端开发
- 技术：C#
- 笔记类型：练习笔记
- 章节序号：0751

## 本章内容

工欲善其事，必先利其器，在正式开始写 C# 代码之前，我们需要先在电脑上搭建好开发环境。

C# 开发环境搭建，整个过程并不复杂——只需要安装两样东西：一个运行平台（.NET SDK）和一个代码编辑器，你就可以开始你的 C# 编程之旅了。


## 第一步：了解 .NET 与 C# 的关系

在安装工具之前，我们先搞清楚一个常见的疑问：C# 和 .NET 是同一个东西吗？

不是。它们的关系可以这样理解：

- C# 是你写代码用的编程语言，就像你用来写文章的"文字"。
- .NET 是运行这些代码的平台和工具集，就像让文字得以印刷、传播的"印刷机和纸张"。

你用 C# 写好的程序，必须依赖 .NET 才能在电脑上运行。因此，搭建 C# 开发环境的第一步，就是安装 .NET SDK。

.NET 目前的主流版本是 .NET 8（长期支持版），它支持 Windows、macOS 和 Linux 三大平台，不再像早年那样只能运行在 Windows 上。


## 第二步：安装 .NET SDK

.NET SDK（软件开发工具包）包含了编译器、运行时和各种开发工具，是 C# 开发的基础。安装步骤如下：

- 访问 .NET 官方下载页面：https://dotnet.microsoft.com/download
- 选择最新的 LTS（长期支持）版本，推荐初学者优先选择 LTS 版，稳定且资料丰富。
- 根据你的操作系统（Windows / macOS / Linux）下载对应的安装包，按提示完成安装。

安装完成后，打开命令行（Windows 用"命令提示符"或"PowerShell"，macOS/Linux 用"终端"），输入以下命令验证是否安装成功：

```text
dotnet --version
```

如果输出了一个版本号（如 8.0.xxx），说明 .NET SDK 已经正确安装。


## 第三步：选择一款代码编辑器

有了 .NET SDK，你理论上已经可以用记事本写代码、用命令行编译运行了。但实际开发中，我们都会使用专门的代码编辑器或 IDE（集成开发环境），它们提供代码补全、错误提示、调试等功能，大大提升开发效率。

对于 C# 初学者，推荐以下两款工具：


### ① Visual Studio（推荐 Windows 用户）

Visual Studio 是微软为 C# 量身打造的旗舰 IDE，功能最为完整，调试体验极佳，是目前企业中使用最广泛的 C# 开发工具。

- 优点：功能强大，集代码编写、调试、测试、发布于一体，特别适合开发 Windows 桌面应用和企业级项目。
- 缺点：安装包较大（几 GB），启动较慢，仅支持 Windows 和 macOS。
- 价格：个人学习使用 Community（社区版）免费，功能已经非常完整。
- 下载地址：https://visualstudio.microsoft.com/zh-hans/downloads/

💡 安装时，在"工作负载"页面勾选 "ASP.NET 和 Web 开发" 或 ".NET 桌面开发"，即可自动安装 C# 所需的全部组件，无需单独配置。


### ② Visual Studio Code（推荐跨平台用户）

VS Code 是一款轻量级的代码编辑器，体积小、启动快，支持 Windows、macOS 和 Linux。通过安装 C# 扩展插件，同样可以获得完善的 C# 开发体验。

- 优点：轻量灵活，跨平台，插件生态丰富，适合追求简洁环境的开发者。
- 缺点：需要手动安装插件，部分高级调试功能不如 Visual Studio 完善。
- 价格：完全免费开源。
- 下载地址：https://code.visualstudio.com/

💡 安装 VS Code 后，在扩展商店中搜索并安装 C# Dev Kit 插件（微软官方出品），即可获得智能提示、调试、项目管理等完整功能。


### 如何选择？

- 如果你使用 Windows，且主要目标是学习 C# 基础或开发 Windows 应用 → 推荐 Visual Studio Community。
- 如果你使用 macOS 或 Linux，或者希望编辑器更轻量 → 推荐 Visual Studio Code + C# Dev Kit。


### 更多相关工具


## 第四步：写下你的第一个 C# 程序

环境搭好之后，我们来验证一下——用命令行创建并运行一个最简单的 C# 项目：

打开命令行，依次执行以下命令：

```text
dotnet new console -n HelloWorld
cd HelloWorld
dotnet run
```

如果你看到输出：

```text
Hello, World!
```

恭喜你！你的 C# 开发环境已经搭建成功，并且成功运行了第一个程序。


## 在 macOS 和 Linux 上开发 C#

如前所述，现代 .NET（.NET 5 及以上版本）已经原生支持跨平台运行，macOS 和 Linux 用户直接安装 .NET SDK 即可，与 Windows 体验基本一致。

此外，你可能还会听到一个叫 Mono 的东西。Mono 是早期社区推出的 .NET 开源跨平台实现，曾经是 Linux 和 macOS 上运行 C# 的主要方式。但随着微软官方 .NET 的全面跨平台化，Mono 的使用场景已经大幅缩减，目前主要用于 Unity 游戏引擎等特定场合。对于新项目，建议直接使用官方 .NET SDK，无需安装 Mono。

如需了解 Mono 的更多信息，可访问：http://www.mono-project.com/


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C# 开发环境` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
