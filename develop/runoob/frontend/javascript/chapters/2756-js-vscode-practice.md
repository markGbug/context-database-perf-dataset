# JavaScript：JavaScript VScode

- 来源：[JavaScript VScode](https://www.runoob.com/js/js-vscode.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：练习笔记
- 章节序号：2756

## 本章内容

在上一章节中我们已经介绍了 JavaScript 基本概念及实例，本章节我们将介绍 JS 代码的编辑器 -- VScode。

VSCode（全称：Visual Studio Code）是一款由微软开发且跨平台的免费源代码编辑器，VSCode 开发环境非常简单易用。

Visual Studio Code 已经内置了对 JavaScript 功能的支持，包括 JavaScript 的智能感知、调试、格式化等功能。

感知功能如下所示：


### 安装 VS Code

VSCode 安装也很简单，打开官网 https://code.visualstudio.com/，下载软件包，一步步安装即可，安装过程注意安装路径设置、环境变量默认自动添加到系统中，勾选以下所有选项：

VSCode 完整安装教程参考：https://www.runoob.com/vscode/vscode-tutorial.html


## 创建一个 JS 代码文件

打开 VScode，然后点击新建文件：

点击选择语言：

在搜索框输入 js，创建 test.js 文件：

输入代码：

```javascript
console.log("Hello, World!");
```

保存 test.js 文件代码，右击文件名，在集成终端执行以下命令：

```text
# node test.js
Hello, World!        # 输出结果
```

node 是可以运行在 JavaScript 的命令，基于 Chrome V8 引擎的 JavaScript 运行时环境。

更多 Node.js 内容可以参考：Node.js 教程


## 更多相关工具


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `JavaScript VScode` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
