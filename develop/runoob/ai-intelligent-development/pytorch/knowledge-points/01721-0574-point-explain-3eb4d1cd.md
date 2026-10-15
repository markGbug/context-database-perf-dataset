# 知识点 01721：PyTorch：PyTorch GPU / CUDA 加速 - 本章内容

- 来源：[PyTorch GPU / CUDA 加速](https://www.runoob.com/pytorch/pytorch-gpu-cuda.html)
- 来源章节：[0574-pytorch-gpu-cuda-practice.md](../chapters/0574-pytorch-gpu-cuda-practice.md)
- 分类：AI / 智能开发
- 技术：PyTorch
- 所在小节：本章内容
- 知识类型：解释
- 原章节序号：0574

## 原文片段

深度学习的核心操作是大规模矩阵乘法与元素运算。CPU 的设计目标是处理复杂的串行逻辑，核心数通常为 8~64 个；而 GPU 拥有数千个简单并行核心，天然适合这类高度并行的数值计算。PyTorch 通过 NVIDIA 的 CUDA（Compute Unified Device Architecture）框架调用 GPU，可将训练速度提升数十倍乃至百倍。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `本章内容` 这一小节和 `PyTorch GPU / CUDA 加速` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
