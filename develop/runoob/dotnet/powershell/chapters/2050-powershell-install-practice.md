# PowerShell：PowerShell 安装

- 来源：[PowerShell 安装](https://www.runoob.com/powershell/powershell-install.html)
- 分类：.NET
- 技术：PowerShell
- 笔记类型：练习笔记
- 章节序号：2050

## 本章内容

PowerShell 自从 6.0 起实现了完全开源和跨平台（PowerShell Core / PowerShell 7+），可运行于 Windows、Linux 和 macOS。


## 一、Windows 上安装 PowerShell 7+


### 方法一：使用 MSI 安装包（推荐）

- 打开 PowerShell 官方 GitHub 发布页： 👉 https://github.com/PowerShell/PowerShell/releases
- 找到最新版本，下载适用于 Windows 的 .msi 安装包
- 双击安装，默认路径安装即可
- 安装完成后，搜索 "PowerShell 7" 打开即可（不会覆盖 Windows PowerShell）


### 方法二：使用命令行（Winget）

适用于 Windows 10/11 且安装了 Windows 包管理器：

```text
winget install --id Microsoft.Powershell --source winget
```

可选参数：--silent 表示静默安装，--version 7.4.1 可指定版本


## 二、Linux 上安装 PowerShell


### Ubuntu / Debian

```text
# 安装依赖
sudo apt update
sudo apt install -y wget apt-transport-https software-properties-common

# 导入微软 GPG 密钥
wget -q https://packages.microsoft.com/config/ubuntu/22.04/packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb

# 安装 PowerShell
sudo apt update
sudo apt install -y powershell
```

启动 PowerShell：

```text
pwsh
```


### CentOS / RHEL / Fedora

```text
# 添加 Microsoft YUM 源
sudo dnf install -y https://packages.microsoft.com/config/rhel/8/packages-microsoft-prod.rpm

# 安装 PowerShell
sudo dnf install -y powershell
```

或 CentOS 7 使用 yum：

```text
sudo yum install -y powershell
```


### Arch Linux / Manjaro

```text
sudo pacman -S powershell
```

如果找不到，可使用 AUR 包管理器（如 yay）


## 三、macOS 上安装 PowerShell


### 方法一：使用 Homebrew（推荐）

```text
brew install --cask powershell
```

启动 PowerShell：

```text
pwsh
```


### 方法二：手动下载 PKG 安装包

- 前往 GitHub 发布页 👉 https://github.com/PowerShell/PowerShell/releases
- 下载 .pkg 安装文件（如 powershell-7.4.1-osx-x64.pkg）
- 双击安装并根据引导完成


## 四、安装验证与卸载


### 验证是否安装成功

```text
pwsh --version
```


### 卸载 PowerShell


## 不同平台启动命令


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PowerShell 安装` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
