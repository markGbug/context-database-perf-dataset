# LaTeX：LaTeX 常用宏包与技巧

- 来源：[LaTeX 常用宏包与技巧](https://www.runoob.com/latex/latex-latex-packages.html)
- 分类：DevOps / 工程化
- 技术：LaTeX
- 笔记类型：练习笔记
- 章节序号：1805

## 本章内容

前几个章节用到的宏包已经不少，本篇做个系统收口：宏包速查、自定义命令、代码排版、多文件工程、latexmk 与排错心法。

掌握这些「工具箱」内容，你就从会写 LaTeX 进化到会管理 LaTeX 项目。


## 常用宏包速查

宏包用 \usepackage[选项]{宏包名} 加载，全部放在导言区。

本地环境提示 File 'xxx.sty' not found 时，用 tlmgr install xxx 安装（TeX Live），MiKTeX 则会自动下载。Overleaf 自带几乎所有宏包，无此烦恼。


## 自定义命令：\newcommand

当同样的内容写了三遍以上，就该定义命令了。\newcommand{\命令名}[参数个数]{定义}。


## 实例：三种自定义命令

自定义环境的语法一并认识一下：


## 实例：自定义「注意」环境


## 代码排版：listings 宏包

技术文档里贴代码，用 listings 宏包，语言高亮、行号、边框全自动。


## 实例：带高亮和行号的代码块

lstlisting 是「原样环境」：内部内容不做任何 LaTeX 解释，&、% 都不用转义。caption 同样自动编号（Listing 1）。常见语言名有 Python、C、Java、HTML、SQL、bash 等，不指定 language 则纯文本着色。

listings 对 UTF-8 中文的支持依赖编译器：XeLaTeX 下中文注释正常；老引擎（latex/pdfLaTeX）下会乱码。中文文档请坚持用 XeLaTeX 编译。


## 多文件工程：\input 与 \include

文档超过几百行就该拆文件——main.tex 只做骨架，内容分而治之。


## 实例：main.tex 骨架

两条命令看着相似，行为有明确分工。

常见坑：\include 会强制换页，用它拼「同一页的几个小节」会发现莫名分页——小片段一律用 \input。


## latexmk：一键编译

第 9 篇的四遍编译流水线，手动敲四条命令很折磨人，latexmk 全自动代劳。

```text
$ latexmk -xelatex main.tex     # XeLaTeX 引擎编译，自动跑满所有遍数
$ latexmk -xelatex -c main.tex  # 清理中间文件（保留 PDF）
$ latexmk -xelatex -C main.tex  # 连 PDF 一起清理
```

latexmk 会自动判断：有 .bib 就跑 bibtex，目录引用有变动就多编译几遍，直到所有编号稳定。编辑器里配置「构建命令」为 latexmk，是本地环境的最佳实践。


## 排错心法

LaTeX 报错信息以叹号开头、附带行号，格式固定，看懂前几行就够了。

```text
! Undefined control sequence.
l.42 \secton{方法}
```

l.42 指出出错行号——本例第 42 行把 \section 拼成了 \secton。修这一处，后面一串连锁错误往往一起消失。

永远只修日志里的第一个错误——后面的错误多半是第一个错误的连锁反应。修完重编译，比一口气改十处靠谱得多。


## 小结


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `LaTeX 常用宏包与技巧` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
