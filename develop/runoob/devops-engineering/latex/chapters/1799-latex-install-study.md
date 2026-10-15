# LaTeX：LaTeX 安装与配置

- 来源：[LaTeX 安装与配置](https://www.runoob.com/latex/latex-install.html)
- 分类：DevOps / 工程化
- 技术：LaTeX
- 笔记类型：学习笔记
- 章节序号：1799

## 本章内容

LaTeX 是一种基于 TeX 的排版系统，使用前需要安装 TeX 发行版和编辑器。

本章将介绍LaTeX 安装与配置，适用于 Windows、macOS 和 Linux 系统。


## LaTeX 的安装


### Windows 系统

在 Windows 系统上，推荐使用 MiKTeX 或 TeX Live 来安装 LaTeX。

- 下载 MiKTeX：访问 MiKTeX 官方网站，下载适合你系统的安装程序。
- 运行安装程序：双击下载的安装程序，按照提示进行安装。建议选择"完整安装"以确保所有常用宏包都已安装。
- 配置环境变量：安装完成后，确保 MiKTeX 的 bin 目录已添加到系统的 PATH 环境变量中。这样可以在命令行中直接使用 LaTeX 命令。
- 下载 TeX Live：访问 TeX Live 官方网站，下载适合你系统的安装程序。
- 运行安装程序：双击下载的安装程序，按照提示进行安装。TeX Live 的安装过程较为耗时，因为它包含了大量的宏包和工具。
- 配置环境变量：安装完成后，确保 TeX Live 的 bin 目录已添加到系统的 PATH 环境变量中。


### macOS 系统

在 macOS 系统上，推荐使用 MacTeX 来安装 LaTeX。

- 下载 MacTeX：访问 MacTeX 官方网站，下载适合你系统的安装程序。
- 运行安装程序：双击下载的 .pkg 文件，按照提示进行安装。MacTeX 包含了 TeX Live 和相关的 GUI 工具。
- 配置环境变量：安装完成后，确保 TeX Live 的 bin 目录已添加到系统的 PATH 环境变量中。


### Linux 系统

在 Linux 系统上，推荐使用 TeX Live 来安装 LaTeX。

- 使用包管理器安装：大多数 Linux 发行版都提供了 TeX Live 的包。你可以使用包管理器来安装。例如，在 Ubuntu 上可以使用以下命令： sudo apt-get install texlive-full 这将安装完整的 TeX Live 发行版，包括所有常用的宏包和工具。
- 手动安装：如果你需要最新版本的 TeX Live，可以从 TeX Live 官方网站 下载安装脚本并手动安装。


## LaTeX 的配置


### 编辑器选择

LaTeX 文档是纯文本文件，因此你可以使用任何文本编辑器来编写 LaTeX 代码。然而，使用专门的 LaTeX 编辑器可以提高效率。以下是一些常用的 LaTeX 编辑器：

- TeXstudio：跨平台的 LaTeX 编辑器，功能强大，适合初学者和高级用户。
- Overleaf：在线 LaTeX 编辑器，无需安装，适合协作和快速编辑。
- VS Code：通用代码编辑器，通过安装 LaTeX 插件（如 LaTeX Workshop）可以支持 LaTeX 编辑和编译。


### 编译 LaTeX 文档

LaTeX 文档需要通过编译生成最终的 PDF 文件。常用的编译命令有：

- pdflatex：生成 PDF 文件，适合大多数文档。
- xelatex：支持 Unicode 和 TrueType 字体，适合处理中文文档。
- lualatex：基于 Lua 的编译引擎，支持现代字体和高级功能。

编译命令的使用方式如下：

```text
pdflatex mydocument.tex
```

这将生成 mydocument.pdf 文件。


### 处理中文文档

如果你需要处理中文文档，推荐使用 xelatex 或 lualatex 编译引擎，并配合 ctex 宏包。以下是一个简单的 LaTeX 中文文档示例：


## 实例

使用 xelatex 编译该文档：

```text
xelatex mydocument.tex
```


### 安装和管理宏包

LaTeX 的宏包可以通过包管理器进行安装和管理。在 MiKTeX 和 TeX Live 中，可以使用以下命令来安装宏包：

- MiKTeX：使用 MiKTeX Console 来搜索和安装宏包。
- TeX Live：使用 tlmgr 命令来安装宏包。例如： tlmgr install <package-name>


## 编译流程

LaTeX 的核心工作流程是：

```text
你编写的 .tex 源文件  →  编译器（如 pdfLaTeX）  →  生成 .pdf 文件
```

编译过程中还会生成一些辅助文件（如 .aux、.log、.toc），它们用于记录目录、引用等信息，通常不需要手动管理。

常见的编译命令有：

- pdflatex：最常用，直接生成 PDF，但对中文和字体支持较弱
- xelatex：支持系统字体和中文，推荐中文用户使用
- lualatex：功能更强大的新一代引擎，速度稍慢


### 第一个 "Hello World" 文档

新建一个 .tex 文件，输入以下内容：

```text
\documentclass{article}

\begin{document}

Hello, World! 这是我的第一份 LaTeX 文档。

\end{document}
```

保存后点击编译，你将得到一份包含这句话的 PDF 文档。


### 文档基本结构解析

一份 LaTeX 文档通常分为两部分：

```text
\documentclass{article}   % 前导区（Preamble）：设置文档类型、加载宏包

\begin{document}          % 正文区：实际显示的内容
    正文内容写在这里
\end{document}
```

- 前导区：位于 \documentclass 与 \begin{document} 之间，用于声明文档类型、引入宏包、定义全局设置，这部分内容不会显示在最终 PDF 中
- 正文区：\begin{document} 到 \end{document} 之间的内容才是真正会被排版输出的部分


### 常用文档类（Document Class）

```text
\documentclass{article}   % 文章、短报告，无章节 chapter
\documentclass{report}    % 长报告，支持 chapter
\documentclass{book}      % 书籍，支持双面排版、chapter
\documentclass{letter}    % 信件
\documentclass{beamer}    % 演示文稿（幻灯片）
```

可以通过方括号传入选项，例如：

```text
\documentclass[12pt, a4paper]{article}
```

这表示使用 12pt 字号、A4 纸张排版。


## 文档的基本结构

每个 LaTeX 文档都由两部分组成：导言区和正文区。

\begin{document} 之前是导言区，用来声明文档类、加载宏包、定义标题作者等全局设置。

\begin{document} 与 \end{document} 之间是正文区，标题、章节、文字、公式都写在这里。

文档类决定了文档的整体形态，在第一行 \documentclass 中声明。

文档类还可以带方括号选项，比如指定字号和纸张：


## 实例：带选项的文档类


## 第一个完整文档

Hello World 太简单，看不出 LaTeX 的价值。下面这份文档加入了标题区、列表和公式，更接近日常使用。


## 实例：第一个完整文档

编译后的效果：

注意几个细节：\maketitle 把导言区定义的标题信息渲染成标题区；\today 自动生成了「2026 年 8 月 20 日」，无需手写；itemize 列表自动加了圆点。

这些命令的具体规则，会在后续几篇里逐一展开。


## 常见问题排查

第一次搭环境，遇到问题是常态。下面收集了新手最高频的报错。


## 复习重点

- 能说明 `LaTeX 安装与配置` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
