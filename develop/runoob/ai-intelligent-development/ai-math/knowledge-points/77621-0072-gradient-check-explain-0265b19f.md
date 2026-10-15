# 知识点 77621：AI 数学基础：链式法则 - 梯度检查（Gradient Check）

- 来源：[链式法则](https://www.runoob.com/ai-math/chain-rule.html)
- 来源章节：[0072-chain-rule-practice.md](../chapters/0072-chain-rule-practice.md)
- 分类：AI / 智能开发
- 技术：AI 数学基础
- 所在小节：梯度检查（Gradient Check）
- 知识类型：解释
- 原章节序号：0072

## 原文片段

如果你手写了一个自定义层或损失函数，怎样验证反向传播的梯度计算正确？用数值梯度 \( (f(x+h)-f(x-h))/2h \) 作为「真值」，与 autograd 算出的梯度对比。相对误差应小于 1e-5。这是 PyTorch 中 torch.autograd.gradcheck 的原理。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `梯度检查（Gradient Check）` 这一小节和 `链式法则` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
