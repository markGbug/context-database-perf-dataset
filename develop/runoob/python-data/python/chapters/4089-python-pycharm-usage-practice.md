# Python：Python PyCharm 安装使用

- 来源：[Python3 Pycharm](https://www.runoob.com/python3/python-pycharm-usage.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4089

## 本章内容

PyCharm 是 JetBrains 出品的 Python 集成开发环境（IDE），拥有智能代码补全和图形化调试功能，支持 Windows /macOS/ Linux 全平台。。

PyCharm 是一套写代码、跑程序、排错、管理项目、协作一体化工具，是目前行业最主流的 Python 开发工具。

本章节我们将介绍 Python 和 PyCharm 的安装，并创建运行你的第一个 Python 程序。


## 安装 Python

Python 是运行 Python 程序所必需的解释器，PyCharm 依赖它来执行代码。

安装 Python 分为三步：下载安装包、执行安装、验证安装结果。


### 下载 Python

打开浏览器，访问 Python 官方网站的下载页面：https://www.python.org/downloads/。

网站通常会自动检测你的操作系统（Windows / macOS / Linux），点击页面上的黄色按钮即可下载最新版本。

建议选择 Python 3.10 及以上版本，目前主流教程和第三方库对新版本支持较好，Python 2.x 已于 2020 年停止维护，不要再使用。


### 安装 Python

以下以 Windows 系统为例，macOS 和 Linux 用户参见对应说明。

Windows 安装步骤：

关键一步：在安装界面底部勾选 Add python.exe to PATH，否则命令行可能找不到 Python

macOS 用户：

可以直接双击 .pkg 安装包按提示完成安装，也可以通过 Homebrew 包管理器安装：

```text
brew install python3
```


### 验证安装

打开命令行工具（Windows 下使用命令提示符或 PowerShell，macOS 下使用终端），输入以下命令：

```text
python --version
```

如果显示类似 Python 3.12.0 的版本号，说明安装成功。

部分系统（尤其是 macOS/Linux）中系统自带的 python 命令指向 Python 2，此时需要输入 python3 --version 来检查新安装的 Python 3。


## 安装 PyCharm

PyCharm 由 JetBrains 公司开发，是目前最流行的 Python IDE 之一。

它分为两个版本，初学者选择免费的社区版即可：


### 下载 PyCharm

访问 JetBrains 官网的 PyCharm 下载页面：https://www.jetbrains.com/pycharm/download/。

在页面中找到 Download 按钮，点击对应操作系统的下载按钮。


### 安装 PyCharm

不同操作系统的安装方式如下：

Linux Snap 安装命令：

```text
sudo snap install pycharm-community --classic
```

安装完成后打开 PyCharm，首次启动会引导你选择 UI 主题和快捷键方案，保持默认设置或按个人喜好选择即可。


### 安装 PyCharm

- 双击下载的安装文件（.exe）。
- 在安装向导中，选择安装路径，建议使用默认路径。
- 勾选 创建桌面快捷方式（Creat Desktop Shortcut）以便快速启动 PyCharm。
- 点击 安装（Install） 开始安装。
- 安装完成后，点击 完成（Finish） 退出安装向导。


### macOS 系统

- 打开下载的 .dmg 文件。
- 将 PyCharm 图标拖拽到 "Applications" 文件夹中。
- 在 "Applications" 文件夹中找到 PyCharm，双击启动。


### Linux 系统

- 解压下载的 .tar.gz 文件。 tar -xzf pycharm-*.tar.gz
- 进入解压后的目录，找到 bin 文件夹。 cd pycharm-*/bin
- 运行 pycharm.sh 启动 PyCharm。 ./pycharm.sh


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python3 Pycharm` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
