# 知识点 50862：PyTorch：PyTorch Autograd - 3、grad_fn 与计算图

- 来源：[PyTorch Autograd](https://www.runoob.com/pytorch/pytorch-autograd.html)
- 来源章节：[0573-pytorch-autograd-practice.md](../chapters/0573-pytorch-autograd-practice.md)
- 分类：AI / 智能开发
- 技术：PyTorch
- 所在小节：3、grad_fn 与计算图
- 知识类型：解释
- 原章节序号：0573

## 原文片段

每个由运算产生的张量都会记录一个 grad_fn，指向创建它的操作节点。这就是计算图的"骨架"：

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `3、grad_fn 与计算图` 这一小节和 `PyTorch Autograd` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
