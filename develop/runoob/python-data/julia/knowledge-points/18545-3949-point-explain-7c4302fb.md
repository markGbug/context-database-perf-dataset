# 知识点 18545：Julia：Julia 运行外部程序 - 实例

- 来源：[Julia 运行外部程序](https://www.runoob.com/julia/julia-external-programs.html)
- 来源章节：[3949-julia-external-programs-practice.md](../chapters/3949-julia-external-programs-practice.md)
- 分类：Python / 数据科学
- 技术：Julia
- 所在小节：实例
- 知识类型：解释
- 原章节序号：3949

## 原文片段

注意：与 Shell 不同，反引号本身不会立即执行命令，而是创建一个 Cmd 对象。Julia 运行命令时不经过 Shell，而是直接 fork/exec 子进程，因此没有通配符展开、管道符等 Shell 特性，也不会有引号转义问题。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `实例` 这一小节和 `Julia 运行外部程序` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
