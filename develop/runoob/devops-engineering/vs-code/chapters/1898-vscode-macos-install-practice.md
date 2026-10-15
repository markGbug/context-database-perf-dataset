# VS Code：VSCode macOS 安装

- 来源：[VSCode macOS 安装](https://www.runoob.com/vscode/vscode-macos-install.html)
- 分类：DevOps / 工程化
- 技术：VS Code
- 笔记类型：练习笔记
- 章节序号：1898

## 本章内容

VSCode 是微软开发的跨平台免费源代码编辑器，支持 Windows、macOS 和 Linux。

在安装 VS Code 之前，请确保您的设备满足以下最低要求：

VS Code 官方网站下载页面：https://code.visualstudio.com/Download。

默认情况下访问 VS Code 官网 https://code.visualstudio.com/，页面会根据你的系统自动匹配安装包，比如我是 macOS，就会出现 Download for macOS 按钮：


## 在 macOS 上安装

访问 VS Code 官网 https://code.visualstudio.com/，点击 "Download for macOS"，会下载一个 VSCode-darwin-universal.zip 的压缩包，解压后是一个 Visual Studio Code 。

将 Visual Studio Code.app 拖到"Applications(应用程序)"文件夹中，使其在 macOS Launchpad(启动台) 中可用。

按下 Command ⌘ 按键，然后按下空格键，在搜索框查找 'Visual'，点击 Visual Studio Code 按钮即可打开:

也可以在启动台查找 Visual Studio Code 图标，找到 Visual Studio Code 图标后，单击它：

Mac OS 将提示是否确认打开从互联网下载的程序，单击 Open 按钮即可：

启动 Visual Studio Code，界面如下：


## VSCode 的 code 命令

启用 VSCode 的 code 命令 非常简单，先打开命令面板：

- macOS 系统快捷键：⇧⌘P
- Windows/Linux 快捷键: Ctrl + Shift + P

搜索安装 >shell command:

然后选择 Shell Command: Install 'code' command in PATH 即可为系统 PATH 路径添加了 code 命令的引用。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `VSCode macOS 安装` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
