# PowerShell：PowerShell 核心概念

- 来源：[PowerShell 核心概念](https://www.runoob.com/powershell/powershell-core.html)
- 分类：.NET
- 技术：PowerShell
- 笔记类型：练习笔记
- 章节序号：2051

## 本章内容

PowerShell 不只是一个命令行工具，它的设计理念、功能架构和使用方式与传统 Shell 有着显著区别。


## 一、Cmdlet：最小命令单元


### 什么是 Cmdlet？

Cmdlet（发音为 command-let）是 PowerShell 中最基本的命令单元，它们都是基于 .NET 的类，运行后会返回一个或多个 .NET 对象。


### 命名规则：动词-名词

每个 Cmdlet 都遵循 动词-名词 命名规范，例如：

PowerShell 附带了数百个 Cmdlet，且第三方模块可以自定义更多。


### 示例

```text
Get-Service
Get-ChildItem -Path C:\Windows
```

你也可以使用 Get-Command 查看所有可用的 Cmdlet：

```text
Get-Command -CommandType Cmdlet
```


## 二、对象管道（Object Pipeline）


### 和 UNIX/Linux 的管道有啥区别？

在传统 Shell 中，管道 (|) 传递的是文本字符串。而在 PowerShell 中，管道传递的是完整的 .NET 对象。

这就意味着你可以保留结构化数据（属性、方法）进行后续处理。


### 示例：按 CPU 使用率过滤进程

```text
Get-Process | Where-Object { $_.CPU -gt 100 } | Select-Object Name, CPU
```

上述命令中：

- Get-Process 获取所有进程（返回对象）
- Where-Object 过滤 CPU 使用率大于 100 的进程
- Select-Object 只输出 Name 和 CPU 字段


### 管道传值之美

你不需要使用 awk、cut、grep 等工具去"解析"输出，而是直接操作对象属性。


## 三、Provider 和 PSDrive：资源驱动器抽象

PowerShell 提供了一种统一的资源访问方式：Provider 模型，它把各种资源映射为虚拟驱动器（PSDrive），就像 C: 盘一样操作。


### 常见 Provider 类型


### 示例：操作注册表

```text
Get-ChildItem HKLM:\Software\Microsoft
```

就像浏览文件夹一样浏览注册表。


## 四、脚本与模块：组织与复用


### 脚本（.ps1）

- PowerShell 脚本是以 .ps1 为扩展名的文本文件
- 包含一系列命令、流程控制、函数等


### 模块（.psm1 / .psd1）

模块是 PowerShell 中用于复用的功能单元，它可以是：

- 一个 .psm1 文件（模块脚本）
- 一个包含 .psd1 清单的文件夹（高级模块）

模块可支持：

- 自动加载（当使用其中函数时自动加载）
- 版本控制
- 依赖声明

查看系统中所有模块：

```text
Get-Module -ListAvailable
```

导入模块：

```text
Import-Module Az
```


## 五、执行策略（Execution Policy）

为了防止恶意脚本执行，PowerShell 引入了 执行策略（Execution Policy），它限制 .ps1 脚本文件的执行行为。


### 常见策略类型


### 设置执行策略

```text
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

⚠️ 注意：执行策略只影响脚本文件，不限制手动输入的命令。


## 六、远程管理（PowerShell Remoting）

PowerShell Remoting 支持通过 WS-MAN（基于 WinRM） 或 SSH 协议，远程连接到另一台计算机并执行命令。


### 启用 WinRM（Windows 上）

```text
Enable-PSRemoting -Force
```


### 常用命令

```text
# 建立远程会话
Enter-PSSession -ComputerName Server01

# 批量执行命令
Invoke-Command -ComputerName Server01,Server02 -ScriptBlock { Get-Service }
```


### 支持 SSH 的跨平台远程

```text
Enter-PSSession -HostName linux01 -User user1 -SSHTransport
```


## 七、Desired State Configuration（DSC）

DSC（Desired State Configuration）是 PowerShell 的声明式配置平台，用于定义系统的"理想状态"。

它允许你：

- 用配置脚本定义资源状态（如某服务应启动、某文件应存在）
- 自动将机器配置为该状态
- 检查偏离并自动修复


### 使用方式

- 编写配置文件（.ps1）
- 编译成 MOF 文件
- 使用 Push 或 Pull 模式部署

DSC 特别适用于大规模服务器配置、合规检查和自动化部署。


## 八、命令发现与帮助系统

PowerShell 提供了丰富的帮助系统，让你可以轻松探索命令：

- Get-Help Get-Process：查看命令帮助
- Get-Command：列出所有命令
- Get-Member：查看对象属性与方法
- Get-Help about_*：查看内置知识文档（如 about_Execution_Policies）


## 后续章节

- 示例：查看对象结构
- 总结

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PowerShell 核心概念` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
