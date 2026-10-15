# PowerShell：PowerShell 简介

- 来源：[PowerShell 简介](https://www.runoob.com/powershell/powershell-intro.html)
- 分类：.NET
- 技术：PowerShell
- 笔记类型：学习笔记
- 章节序号：2049

## 本章内容

在大多数人印象中，Windows 的命令行工具要么是年代久远的 cmd，要么是让人头秃的"图形界面点来点去"。但其实，微软早在 2006 年就推出了一款功能强大、专为系统管理员设计的现代命令行工具 —— PowerShell。

PowerShell 是微软推出的跨平台（Windows / Linux / macOS）自动化与配置管理框架，由「命令行外壳（host）」和「脚本语言」两部分组成。

PowerShell 基于 .NET（完整 .NET Framework 或 .NET Core / .NET 6+），因此能直接调用数以千计的 .NET API，并原生支持面向对象管道（object pipeline），而非传统 Shell 的纯文本流。

PowerShell 构建在 .NET Framework 之上，专为系统管理员和高级用户设计，用于自动化各种系统管理任务。


### PowerShell 的核心特点

- 面向对象：不同于传统命令行工具处理文本，PowerShell 直接处理 .NET 对象
- 强大的管道功能：可以轻松地将一个命令的输出传递给另一个命令
- 可扩展性：可以创建自定义 cmdlet（命令）和模块
- 跨平台支持：PowerShell Core 可在 Windows、Linux 和 macOS 上运行


## 发展历史

在 UNIX 系统里，像 bash、sh、csh 这些壳程序（Shell）早就是系统管理员的得力助手了。而 Windows 之前在这方面一直欠缺，直到 PowerShell 的出现，才算是补上了这块短板。它不仅能像 UNIX Shell 一样执行命令，还集成了脚本语言和各种辅助工具，自动化能力更上一层楼。


## PowerShell 与传统命令行对比


## 什么人员适合学习？

- 系统管理员：批量管理服务器、自动化部署、配置控制
- 开发人员：构建 DevOps 流程、脚本工具、测试工具链
- 数据分析师：自动处理日志、提取数据、系统集成
- 初学者：学习命令行编程、了解操作系统底层机制

PowerShell 不只是一个命令行工具，它更像是一种高级自动化平台。不论你是运维人员、开发者，还是想精通 Windows 系统的普通用户，PowerShell 都值得你深入了解和掌握。

它比 cmd 灵活，比 bash 强大，最关键的是——它正在以跨平台的姿态，成为新时代的自动化基础设施工具。


## 复习重点

- 能说明 `PowerShell 简介` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
