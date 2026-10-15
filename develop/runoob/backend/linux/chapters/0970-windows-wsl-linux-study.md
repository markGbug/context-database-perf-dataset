# Linux：Windows WSL 安装 Linux

- 来源：[WSL 安装 Linux](https://www.runoob.com/linux/windows-wsl-linux.html)
- 分类：后端开发
- 技术：Linux
- 笔记类型：学习笔记
- 章节序号：0970

## 本章内容

WSL（Windows Subsystem for Linux） 是微软为 Windows 用户提供的一个子系统，它允许你在 Windows 上原生运行 Linux（不是虚拟机，不是双系统），直接使用 Bash、apt、gcc、Python、Node.js 等 Linux 工具。


### WSL 的版本区别

推荐使用 WSL2，兼容性更强，功能更完整。


## 安装步骤（以 WSL2 为例）


### 前提条件

- Windows 10 2004（或更高版本） / Windows 11
- 启用虚拟化（BIOS 中 VT-x 或 AMD-V 开启）


### 方法一：一键安装（推荐）

```text
wsl --install
```

该命令会自动：

- 启用 WSL 功能
- 安装 WSL2 内核
- 安装默认的 Ubuntu
- 设置为 WSL2

安装完后，重启一次系统即可。


### 方法二：手动安装（适合定制需求）

1、启用 WSL 功能和虚拟机平台

```text
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

2、下载并安装 Linux 内核更新包

👉 下载地址：https://aka.ms/wsl2kernel

3、设置默认 WSL 版本为 WSL2

```text
wsl --set-default-version 2
```

4、从 Microsoft Store 安装 Linux 发行版（如 Ubuntu）

也可命令行方式安装：

```text
wsl --install -d Ubuntu
```


## 常用命令速查表


## 日常使用指南

如何访问 Windows 文件？

在 WSL 中，Windows 文件挂载在 /mnt/c、/mnt/d 等目录：

```text
cd /mnt/c/Users/你的用户名/Desktop
```

如何访问 WSL 文件？

在 Windows 中访问：

```text
\\wsl$\Ubuntu\home\your_username
```

或者在资源管理器地址栏输入：\\wsl$


## 配套推荐工具


## 如何卸载或重置？

```text
# 卸载某个 Linux 发行版
wsl --unregister Ubuntu

# 重置 WSL 所有数据（危险操作）
wsl --unregister <发行版名>
```


## 复习重点

- 能说明 `WSL 安装 Linux` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
