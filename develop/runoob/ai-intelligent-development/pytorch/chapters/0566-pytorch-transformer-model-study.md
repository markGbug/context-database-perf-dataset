# PyTorch：PyTorch 构建 Transformer 模型

- 来源：[PyTorch Transformer](https://www.runoob.com/pytorch/pytorch-transformer-model.html)
- 分类：AI / 智能开发
- 技术：PyTorch
- 笔记类型：学习笔记
- 章节序号：0566

## 本章内容

Transformer 是现代机器学习中最强大的模型之一。

Transformer 模型是一种基于自注意力机制（Self-Attention） 的深度学习架构，它彻底改变了自然语言处理（NLP）领域，并成为现代深度学习模型（如 BERT、GPT 等）的基础。

Transformer 是现代 NLP 领域的核心架构，凭借其强大的长距离依赖建模能力和高效的并行计算优势，在语言翻译和文本摘要等任务中超越了传统的 长短期记忆 (LSTM) 网络。

如果你还不了解 Transformer，可以参考：Transformer 模型介绍。


## 使用 PyTorch 构建 Transformer 模型

构建 Transformer 模型的步骤如下：


### 1、导入必要的库和模块

导入 PyTorch 核心库、神经网络模块、优化器模块、数据处理工具，以及数学和对象复制模块，为定义模型架构、管理数据和训练过程提供支持。

```text
import torch
import torch.nn as nn
import torch.optim as optim
import torch.utils.data as data
import math
import copy
```

说明：

- torch：PyTorch 的核心库，用于张量操作和自动求导。
- torch.nn：PyTorch 的神经网络模块，包含各种层和损失函数。
- torch.optim：优化算法模块，如 Adam、SGD 等。
- math：数学函数库，用于计算平方根等。
- copy：用于深度复制对象。


### 定义基本构建块：多头注意力、位置前馈网络、位置编码

多头注意力通过多个"注意力头"计算序列中每对位置之间的关系，能够捕捉输入序列的不同特征和模式。

MultiHeadAttention 类封装了 Transformer 模型中常用的多头注意力机制，负责将输入拆分成多个注意力头，对每个注意力头施加注意力，然后将结果组合起来，这样模型就可以在不同尺度上捕捉输入数据中的各种关系，提高模型的表达能力。


## 实例

说明：

- 多头注意力机制：将输入分割成多个头，每个头独立计算注意力，最后将结果合并。
- 缩放点积注意力：计算查询和键的点积，缩放后使用 softmax 计算注意力权重，最后对值进行加权求和。
- 掩码：用于屏蔽无效位置（如填充部分）。


### 位置前馈网络（Position-wise Feed-Forward Network）


## 实例

前馈网络：由两个全连接层和一个 ReLU 激活函数组成，用于进一步处理注意力机制的输出。


### 位置编码

位置编码用于注入输入序列中每个 token 的位置信息。

使用不同频率的正弦和余弦函数来生成位置编码。


## 实例


### 构建编码器块（Encoder Layer）

编码器层：包含一个自注意力机制和一个前馈网络，每个子层后接残差连接和层归一化。


## 实例


### 构建解码器模块

解码器层：包含一个自注意力机制、一个交叉注意力机制和一个前馈网络，每个子层后接残差连接和层归一化。


## 实例


### 构建完整的 Transformer 模型


## 实例

说明：

- Transformer 模型：包含编码器和解码器部分，每个部分由多个层堆叠而成。
- 掩码生成：用于屏蔽无效位置和未来信息。
- 前向传播：依次通过编码器和解码器，最后通过全连接层输出。

模型初始化参数说明：

```text
class Transformer(nn.Module):
    def __init__(
        self,
        src_vocab_size,  # 源语言词汇表大小（如英文单词数）
        tgt_vocab_size,  # 目标语言词汇表大小（如中文单词数）
        d_model=512,     # 模型维度（每个词向量的长度）
        num_heads=8,     # 多头注意力的头数
        num_layers=6,    # 编码器/解码器的堆叠层数
        d_ff=2048,       # 前馈网络隐藏层维度
        max_seq_length=100, # 最大序列长度（用于位置编码）
        dropout=0.1      # Dropout概率
    ):
```


### 训练 PyTorch Transformer 模型

使用随机数据训练模型，计算损失并更新参数。


## 实例


### 模型评估

评估过程：在验证数据上计算损失，评估模型性能。


## 实例


## 复习重点

- 能说明 `PyTorch Transformer` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
