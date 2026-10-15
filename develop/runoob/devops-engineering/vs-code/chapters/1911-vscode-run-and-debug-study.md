# VS Code：VSCode 运行和调试代码

- 来源：[VSCode 运行和调试代码](https://www.runoob.com/vscode/vscode-run-and-debug.html)
- 分类：DevOps / 工程化
- 技术：VS Code
- 笔记类型：学习笔记
- 章节序号：1911

## 本章内容

VS Code 内置了运行和调试 Node.js 应用程序的支持。

本章节，我们将使用上一部分安装的 Python 扩展来调试一个 Python 程序。

接下来就让我们调试前面创建的 hello.py 程序。

调试前确保您的计算机已安装 Python 3。

如果您的计算机上未安装 Python 解释器，窗口右下角会弹出通知。

选择 Select Interpreter（选择解释器） 打开命令面板，从中选择您想使用的 Python 解释器，或安装一个新的解释器。


### 设置断点

在 hello.py 文件中，将光标放置在 print 行上，点击小红点（鼠标移动到红点位置会显示），或者按下 F9 键来设置断点。

编辑器左侧的边距中会出现一个红点，表示已设置断点。

断点可以让您在程序执行到某一行代码时暂停，便于调试。


### 启动调试会话

按下 F5 启动调试会话。

系统会提示选择调试器，选择 Python 调试器。

选择运行当前的 Python 文件：


### 调试代码

程序启动后，执行会在您设置的断点处暂停。

提示：将鼠标悬停在编辑器中的 name 变量上，即可查看其值。在调试视图的 变量视图（Variables View） 中，您可以随时查看变量的值。


### 继续执行程序

在调试工具栏中，点击 Continue（继续） 按钮，或再次按下 F5，以继续执行程序。

VS Code 提供了许多高级的调试功能，例如监视变量（Watch Variables）、条件断点（Conditional Breakpoints）和启动配置（Launch Configurations）。


## 复习重点

- 能说明 `VSCode 运行和调试代码` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
