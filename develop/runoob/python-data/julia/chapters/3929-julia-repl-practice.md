# Julia：Julia 交互式命令窗口

- 来源：[Julia 交互式命令](https://www.runoob.com/julia/julia-repl.html)
- 分类：Python / 数据科学
- 技术：Julia
- 笔记类型：练习笔记
- 章节序号：3929

## 本章内容

执行 julia 命令可以直接进入交互式命令窗口：

```text
$ julia
               _
   _       _ _(_)_     |  Documentation: https://docs.julialang.org
  (_)     | (_) (_)    |
   _ _   _| |_  __ _   |  Type "?" for help, "]?" for Pkg help.
  | | | | | | |/ _` |  |
  | | |_| | | | (_| |  |  Version 1.7.2 (2022-02-06)
 _/ |\__'_|_|_|\__'_|  |  release-1.7/bf53498635 (fork: 461 commits, 259 days)
|__/                   |

julia>
```

执行 exit() 退出交互式命令窗口，也可以通过输入 CTRL-D（同时按 Ctrl 键和 d 键）退出。

输入一段完整的表达式并回车，REPL 会计算并显示它的值：


## 实例

ans 是一个特殊变量，它保存最后一次表达式的计算结果，只在交互式会话中有效。

执行 exit() 退出交互式命令窗口，也可以通过输入 CTRL-D（同时按 Ctrl 键和 d 键）退出。


## REPL 的四种命令模式

Julia REPL 内置了四种工作模式，通过不同的按键切换：

在任意模式下按 Backspace（退格键）或 Ctrl-C 可以返回默认的 Julia 模式。


### 帮助模式

在空提示符下输入 ?，然后输入要查询的函数名即可查看文档，例如查询 println：

```java
help?> println
search: println print printstyled sprint isprint

  println([io::IO], xs...)
  Print (using print) xs followed by a newline.
```

遇到不认识的函数时，用帮助模式查文档是最快的自学方式。


### Shell 模式

输入 ; 进入 Shell 模式后，可以直接执行 ls、cd 等系统命令：

```text
shell> ls
hello.jl  runoob_test.jl
```


### 包管理模式

输入 ] 进入 Pkg 模式后，可以安装和管理软件包：

```text
pkg> add Example        # 安装 Example 包
pkg> rm Example         # 卸载包
pkg> status             # 查看已安装的包
```

包管理的详细用法会在模块与包管理章节介绍。


## 运行 Julia 代码文件

除了交互式使用，我们也可以执行一个 Julia 的代码文件，文件名以 .jl 结尾。

以下是一个名为 runoob_test.jl 的文件：


## runoob_test.jl 文件

要执行 Julia 语言代码可以使用 julia runoob_test.jl 命令。

执行以上代码输出:

```text
$ julia runoob_test.jl
Hello World!
RUNOOB
2
```


### 在 REPL 中加载文件

在 REPL 中可以使用 include() 函数加载并执行一个源文件：


## 实例

注意：include() 会在当前会话中执行文件里的所有代码，适合开发时反复加载调试；而 julia 命令是启动一个新的进程执行文件，适合运行完整程序。


## 常用的 REPL 快捷操作

其中 Tab 补全还支持 Unicode 符号：输入 \pi 后按 Tab 键，会自动变成 π，这是 Julia 的特色功能之一。


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Julia 交互式命令` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
