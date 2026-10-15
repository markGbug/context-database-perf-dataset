# PowerShell：PowerShell 教程

- 来源：[PowerShell 教程](https://www.runoob.com/powershell/powershell-tutorial.html)
- 分类：.NET
- 技术：PowerShell
- 笔记类型：练习笔记
- 章节序号：2048

## 本章内容

PowerShell（包括 Windows PowerShell 和 PowerShell Core）是微软公司开发的一个跨平台的命令行工具和脚本语言，它建立在.NET框架之上。与

PowerShell 由在 .NET Framework 和后来的 .NET 上构建的命令行界面壳层相关脚本语言组成，最初仅仅是 Windows 组件，后于 2016 年 8 月 18 日开源并提供跨平台支持。

PowerShell 是面向对象的，这意味着它处理的不是简单的文本，而是 .NET 对象。


## 谁适合学习 PowerShell？

PowerShell 适合需要高效管理 Windows 系统、自动化重复任务或与微软产品（如 Active Directory、Azure、Exchange 等）交互的技术人员，包括系统管理员、IT 运维、开发者和安全工程师。

PowerShell 的核心优势是将图形界面的点击操作转化为可复用的脚本命令，特别适合批量操作和定期任务。

普通用户若只需基本电脑操作则不必学习 PowerShell。


## 为什么需要 PowerShell？

在 UNIX 世界，bash、zsh、sh 等命令行壳程序早已成为开发与运维人员的标配。然而，Windows 起初只有功能有限的 cmd.exe，缺乏脚本能力、模块化支持与对象处理能力。

PowerShell 的诞生正是为了补齐 Windows 系统在自动化和命令行控制上的短板，而现在，它已经脱离 Windows，成为了一个真正跨平台的自动化工具。


### PowerShell 核心特性

- 面向对象 - 命令输出的是对象（如进程、文件），而非纯文本。
- 管道（Pipeline） - 支持对象传递，可链式处理数据。
- 统一命名规范 - 采用 动词-名词 格式（如 Get-Process）。
- 跨平台支持 - 可在 Windows、Linux、macOS 运行（PowerShell Core）。
- 深度集成 .NET - 可直接调用 .NET 类库和方法。
- 模块化设计 - 功能以模块形式扩展（如 ActiveDirectory 模块）。
- 自动化脚本 - 支持复杂脚本编写（变量、循环、函数等）。
- 远程管理 - 通过 Enter-PSSession 或 Invoke-Command 管理远程机器。
- 别名系统 - 支持简写（如 ls 替代 Get-ChildItem）。
- 强大的帮助系统 - 内置 Get-Help 和示例代码。

一句话总结：PowerShell 是面向对象的自动化工具，专为高效系统管理和跨平台任务设计。


## PowerShell 入门实例


## 实例


## 相关资源

官方文档：https://docs.microsoft.com/powershell/


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PowerShell 教程` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
