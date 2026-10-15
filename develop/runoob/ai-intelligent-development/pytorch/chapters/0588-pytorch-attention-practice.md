# PyTorch：PyTorch 注意力机制

- 来源：[PyTorch 注意力机制](https://www.runoob.com/pytorch/pytorch-attention.html)
- 分类：AI / 智能开发
- 技术：PyTorch
- 笔记类型：练习笔记
- 章节序号：0588

## 本章内容

注意力机制（Attention Mechanism）是深度学习中最重要的概念之一。

注意力机制让模型学会"关注"输入中最相关的部分，在自然语言处理、计算机视觉等领域取得了巨大成功。

本节详细介绍注意力机制的核心原理、PyTorch 实现以及各种注意力变体。

适用版本：本文代码基于 PyTorch 2.0+ 编写。nn.MultiheadAttention 的 batch_first 参数在 PyTorch 1.9 引入，早期版本需要手动处理维度。


## 1. 注意力机制基础


### 1.1 为什么需要注意力

传统的序列到序列（Seq2Seq）模型存在一个根本问题：Encoder 需要将所有信息压缩到一个固定长度的向量中。对于长序列，这个向量会成为信息瓶颈——句子越长，信息丢失越严重。

注意力机制的核心理念是：让 Decoder 在生成每个输出时，能够"看"到 Encoder 的所有隐藏状态，并根据当前上下文动态地分配不同的注意力权重。这就像人类翻译时，每翻译一个词都会回头去看原文的对应部分。


### 1.2 注意力机制的本质

注意力机制可以看作是一种加权求和操作。给定查询（Query）、键（Key）和值（Value），通过计算 Query 与每个 Key 的相似度来分配权重，再对 Value 进行加权求和：

\[\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V\]$$

其中：

- Q（Query）：查询向量，表示"我正在寻找什么信息"
- K（Key）：键向量，表示"我这里有什么信息"（用于匹配）
- V（Value）：值向量，表示"我实际能提供的内容"
- $$d_k$$：Key 的维度，$$\sqrt{d_k}$$ 用于缩放，防止点积值过大导致 softmax 梯度消失

为什么要除以 $$\sqrt{d_k}$$？当 $$d_k$$ 较大时，Q 和 K 的点积的方差会随维度线性增长，导致 softmax 的输入值过大，梯度趋近于零。缩放后使方差恢复到 1，保证梯度正常流动。


## 实例

注意力权重的本质是概率分布——经过 softmax 后，每一行的和为 1。权重越大表示模型对该位置越"关注"。


## 2. PyTorch 注意力模块


### 2.1 Multi-Head Attention

Multi-Head Attention（多头注意力） 允许模型同时关注来自不同位置的不同表示子空间的信息。它将 Q、K、V 分别通过不同的线性投影映射到多个子空间，在每个子空间独立计算注意力，最后拼接结果再做一次线性变换。

这就像让多个人从不同角度同时审视同一段文本——有人关注语法结构，有人关注语义关联，有人关注长距离依赖。多头机制让模型能捕获更丰富的模式。

$$\text{MultiHead}(Q,K,V) = \text{Concat}(\text{head}_1, \dots, \text{head}_h)W^O$$

$$\text{where head}_i = \text{Attention}(QW_i^Q, KW_i^K, VW_i^V)$$


## 实例


### 2.2 PyTorch 内置 MultiheadAttention

PyTorch 提供了经过高度优化的 nn.MultiheadAttention，底层使用了融合算子（fused kernels），在大多数场景下比手动实现更快。推荐在生产环境中使用。


## 实例

注意 mask 类型：nn.MultiheadAttention 的 key_padding_mask 使用 True = 忽略 的约定，与某些自定义实现中 0 = 忽略的约定相反。使用时务必确认。


## 3. 注意力机制的变体


### 3.1 自注意力（Self-Attention）

自注意力 是注意力机制的一种特殊形式——Q、K、V 都来自同一个输入序列。它让序列中的每个位置都能直接关注到所有其他位置，从而捕获全局依赖关系。这是 Transformer 的核心组件，也是它优于 RNN 的关键所在：RNN 需要逐步传递信息，而自注意力一步到位。


## 实例


### 3.2 交叉注意力（Cross-Attention）

交叉注意力 中，Q 来自一个序列（如 Decoder），K 和 V 来自另一个序列（如 Encoder）。这是 Encoder-Decoder 架构的桥梁——让 Decoder 在生成每个 token 时，能动态地"查阅"Encoder 的所有输出。


## 实例

自注意力 vs 交叉注意力：自注意力中 Q/K/V 形状相同（$$seq \times seq$$ 的权重矩阵）；交叉注意力中 Q 长度与 K 长度可以不同（$$target \times source$$ 的权重矩阵）。


### 3.3 位置编码（Positional Encoding）

注意力机制本身具有置换不变性——打乱输入顺序不会改变输出。但语言和图像都是有序的，因此需要通过位置编码显式注入位置信息。原始 Transformer 使用正弦/余弦函数生成固定的位置编码：

$$PE_{(pos, 2i)} = \sin\left(\frac{pos}{10000^{2i/d_{model}}}\right), \quad PE_{(pos, 2i+1)} = \cos\left(\frac{pos}{10000^{2i/d_{model}}}\right)$$


## 实例


## 4. 注意力机制的视觉应用

注意力机制不仅适用于序列数据，在计算机视觉中同样大放异彩。以下介绍三种经典的视觉注意力模块：


### 4.1 通道注意力（Channel Attention）

通道注意力（如 SENet）让网络学习"哪些通道更重要"。它对每个通道进行全局池化压缩空间信息，再通过两层全连接网络学习通道间的依赖关系。


## 实例


### 4.2 空间注意力（Spatial Attention）

空间注意力 让网络学习"哪些位置更重要"。它在通道维度上进行压缩（取均值和最大值），然后用卷积学习空间权重图。


## 实例


### 4.3 CBAM（Convolutional Block Attention Module）

CBAM 将通道注意力和空间注意力串联应用：先通过通道注意力选择重要通道，再通过空间注意力选择重要位置。两者互补，效果优于单独使用。


## 实例


## 5. 注意力机制在 NLP 中的应用


## 后续章节

- 5.1 Transformer Encoder
- 实例
- 5.2 注意力可视化
- 实例
- 6. 完整的注意力分类器
- 6.1 基于注意力的文本分类
- 实例
- 6.2 常见注意力变体对比
- 7. 最佳实践与常见问题
- 7.1 使用技巧
- 7.2 常见问题

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PyTorch 注意力机制` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
