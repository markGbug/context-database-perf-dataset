# PyTorch：PyTorch torch.nn 参考手册

- 来源：[PyTorch torch.nn](https://www.runoob.com/pytorch/pytorch-torch-nn-ref.html)
- 分类：AI / 智能开发
- 技术：PyTorch
- 笔记类型：学习笔记
- 章节序号：0564

## 本章内容

PyTorch 的 torch.nn 模块是构建和训练神经网络的核心模块，它提供了丰富的类和函数来定义和操作神经网络。

以下是 torch.nn 模块的一些关键组成部分及其功能：

1、nn.Module 类：

- nn.Module 是所有自定义神经网络模型的基类。用户通常会从这个类派生自己的模型类，并在其中定义网络层结构以及前向传播函数（forward pass）。

2、预定义层（Modules）：

- 包括各种类型的层组件，例如卷积层（nn.Conv1d, nn.Conv2d, nn.Conv3d）、全连接层（nn.Linear）、激活函数（nn.ReLU, nn.Sigmoid, nn.Tanh）等。

3、容器类：

- nn.Sequential：允许将多个层按顺序组合起来，形成简单的线性堆叠网络。
- nn.ModuleList 和 nn.ModuleDict：可以动态地存储和访问子模块，支持可变长度或命名的模块集合。

4、损失函数（Loss Functions）：

- torch.nn 包含了一系列用于衡量模型预测与真实标签之间差异的损失函数，例如均方误差损失（nn.MSELoss）、交叉熵损失（nn.CrossEntropyLoss）等。

5、实用函数接口（Functional Interface）：

- nn.functional（通常简写为 F），包含了许多可以直接作用于张量上的函数，它们实现了与层对象相同的功能，但不具有参数保存和更新的能力。例如，可以使用 F.relu() 直接进行 ReLU 操作，或者 F.conv2d() 进行卷积操作。

6、初始化方法：

- torch.nn.init 提供了一些常用的权重初始化策略，比如 Xavier 初始化 (nn.init.xavier_uniform_()) 和 Kaiming 初始化 (nn.init.kaiming_uniform_())，这些对于成功训练神经网络至关重要。

7、Transformer 层：

- PyTorch 提供了完整的 Transformer 架构组件，包括 nn.Transformer, nn.TransformerEncoder, nn.TransformerDecoder 以及注意力机制 nn.MultiheadAttention 等。

8、归一化层：


## PyTorch torch.nn 模块参考手册


### 神经网络容器


### 全局钩子（Global Hooks）


### 线性层


### 卷积层


### 池化层


### 填充层（Padding Layers）


### 激活函数（非线性激活 - 加权求和类）


### 激活函数（非线性激活 - 其他）


### 归一化层


### 循环神经网络层


### Transformer 层


### 注意力机制（Attention）


### 嵌入层（稀疏层）


### Dropout 层


### 视觉层（Vision Layers）


### 损失函数


### 距离函数


### 并行层（DataParallel）


### 实用函数（nn.functional）


### 工具函数（nn.utils）


### 参数初始化（nn.init）


### RNN 工具函数


### 剪枝函数（Pruning）


## 后续章节

- Flatten 层
- 实例
- 实例
- 实例：使用 CNN 进行图像分类
- 实例：使用 LSTM 进行文本分类
- 实例：使用 Transformer 编码器

## 复习重点

- 能说明 `PyTorch torch.nn` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
