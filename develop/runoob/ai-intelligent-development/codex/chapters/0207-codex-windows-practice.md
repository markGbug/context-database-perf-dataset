# Codex：Codex Windows 原生支持

- 来源：[Codex Windows](https://www.runoob.com/codex/codex-windows.html)
- 分类：AI / 智能开发
- 技术：Codex
- 笔记类型：练习笔记
- 章节序号：0207

## 本章内容

Codex 在 Windows 上提供原生支持，无需 WSL 即可运行。本节介绍 Windows 平台特有的功能和配置。


## Windows 支持概述

Codex 支持以下 Windows 环境：


## 安装


### 使用 winget 安装


## winget 安装


### 使用 Chocolatey


## Chocolatey 安装


### 手动安装

从 GitHub 下载 Windows 版本：

```text
https://github.com/openai/codex/releases
```

下载 .exe 安装程序并运行。


## 原生沙箱

Codex 可以在 Windows PowerShell 中原生运行：

- 无需 WSL 或虚拟机
- 保持 Windows 工作流程
- 与 Windows 工具无缝集成


### 沙箱模式配置


## 配置沙箱


### 沙箱模式说明


### PowerShell 集成

Codex 可以直接在 PowerShell 中使用：


## PowerShell 中使用


### CMD 支持

Codex 也支持传统的 CMD 环境：


## CMD 中使用


## Windows 特有配置


### 路径处理

Windows 路径与 Unix 不同，Codex 会自动处理：

- 反斜杠转换为正斜杠
- 盘符处理
- UNC 路径支持


### 环境变量


## Windows 环境变量


### 代理配置


## 代理设置


## 故障排除


### 常见问题

- 检查是否安装了必要的 Visual C++ 运行库
- 尝试以管理员权限运行
- 检查杀毒软件是否阻止

确保 PowerShell 可执行文件在 PATH 中。

Codex 支持 Unicode，但某些旧版终端可能有问题。


### 日志位置

Windows 日志位置：

```text
%USERPROFILE%\.codex\log\codex-tui.log
```


## 后续章节

- 与 WSL2 比较
- 最佳实践
- 常见问题
- Q: Windows 原生版本和 WSL 版本哪个好？
- Q: 可以和 WSL 共存吗？
- Q: 需要管理员权限吗？
- Q: 支持 PowerShell ISE 吗？

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Codex Windows` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
