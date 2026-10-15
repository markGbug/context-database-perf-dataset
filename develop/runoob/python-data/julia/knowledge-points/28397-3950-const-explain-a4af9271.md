# 知识点 28397：Julia：Julia 性能技巧 - 避免非 const 的全局变量

- 来源：[Julia 性能技巧](https://www.runoob.com/julia/julia-performance.html)
- 来源章节：[3950-julia-performance-practice.md](../chapters/3950-julia-performance-practice.md)
- 分类：Python / 数据科学
- 技术：Julia
- 所在小节：避免非 const 的全局变量
- 知识类型：解释
- 原章节序号：3950

## 原文片段

全局变量的值（和类型）随时可能改变，编译器无法优化使用它的代码。解决方法：要么用参数传给函数，要么声明为 const：

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `避免非 const 的全局变量` 这一小节和 `Julia 性能技巧` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
