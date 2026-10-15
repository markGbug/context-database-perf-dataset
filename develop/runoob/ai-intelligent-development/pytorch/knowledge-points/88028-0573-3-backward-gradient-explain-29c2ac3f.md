# 知识点 88028：PyTorch：PyTorch Autograd - 3、非标量输出调用 backward(gradient)

- 来源：[PyTorch Autograd](https://www.runoob.com/pytorch/pytorch-autograd.html)
- 来源章节：[0573-pytorch-autograd-practice.md](../chapters/0573-pytorch-autograd-practice.md)
- 分类：AI / 智能开发
- 技术：PyTorch
- 所在小节：3、非标量输出调用 backward(gradient)
- 知识类型：解释
- 原章节序号：0573

## 原文片段

如果输出是一个向量或矩阵而不是标量，backward() 需要传入一个与输出形状相同的 gradient 参数（即"上游梯度"），本质上是计算向量-雅可比积（VJP）：

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `3、非标量输出调用 backward(gradient)` 这一小节和 `PyTorch Autograd` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
