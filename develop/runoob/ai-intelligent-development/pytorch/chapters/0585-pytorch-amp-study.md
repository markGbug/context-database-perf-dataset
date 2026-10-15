# PyTorch：PyTorch 混合精度训练 (AMP)

- 来源：[PyTorch 混合精度训练](https://www.runoob.com/pytorch/pytorch-amp.html)
- 分类：AI / 智能开发
- 技术：PyTorch
- 笔记类型：学习笔记
- 章节序号：0585

## 本章内容

混合精度训练是深度学习中最重要的性能优化技术之一。它通过同时使用 FP32（单精度）和 FP16（半精度）浮点数进行计算，可以在几乎不损失模型精度的前提下，显著提升训练速度并减少显存占用。本节详细介绍 PyTorch 中的自动混合精度（Automatic Mixed Precision，AMP）技术。

适用版本：本文代码基于 PyTorch 1.6+ 的 torch.cuda.amp API 编写。PyTorch 2.4+ 推荐使用 torch.amp.autocast 和 torch.amp.GradScaler，用法基本一致，文中会标注差异。


## 1. 混合精度训练基础


### 1.1 为什么需要混合精度

深度学习模型训练过程中涉及大量的矩阵运算。传统的 FP32（32位浮点）计算精度高，但占用显存大、计算速度慢。FP16（16位浮点）计算速度快、显存占用少，但数值表示范围较小，容易出现梯度下溢（underflow）问题。

混合精度训练的核心理念是：对精度要求高的操作使用 FP32，对精度要求不高的操作使用 FP16。这样既能享受 FP16 的速度优势，又能避免精度问题。

下图展示了三种浮点格式的位布局差异——指数位决定数值范围，尾数位决定精度：


### 1.2 混合精度的优势


### 1.3 Tensor Core 加速原理

NVIDIA 的 Tensor Core 是一种专门用于矩阵运算的硬件单元。它可以在一个时钟周期内完成 4×4 矩阵乘加运算（D = A × B + C），这就是 FP16 训练加速的主要来源。相比普通 CUDA 核心需要多次指令才能完成同样的运算，Tensor Core 将其压缩为单条指令。

支持 Tensor Core 的 GPU 包括：

- Volta 架构（V100）— 首代 Tensor Core，仅支持 FP16
- Turing 架构（RTX 20 系）— 支持 FP16 / INT8 / INT4
- Ampere 架构（RTX 30 系、A100）— 新增 BF16 / TF32 支持
- Ada Lovelace 架构（RTX 40 系）— 新增 FP8 支持
- Hopper 架构（H100）— 新增 FP8 Transformer Engine

消费级 RTX GPU 同样支持 Tensor Core，如 RTX 3060 及以上型号均可享受 AMP 加速。


## 2. PyTorch AMP 基础用法


### 2.1 autocast 与 GradScaler

PyTorch 的 AMP API 主要包含两个核心组件：

- autocast：上下文管理器，自动将区域内的运算切换为 FP16（对精度敏感的操作会自动回退到 FP32）
- GradScaler：动态调整梯度缩放系数，放大 FP16 梯度以防止下溢（仅 FP16 需要，BF16 通常不需要）

下图展示了 AMP 训练一个完整 step 的数据流：


### 2.2 基础使用示例


## 实例

API 迁移提示：PyTorch 2.4 将 torch.cuda.amp.autocast 标记为 deprecated，推荐使用 torch.amp.autocast('cuda')。两者用法完全一致，仅导入路径不同。


### 2.3 BF16 与 FP16 的选择

现代 GPU 支持两种半精度格式，它们的核心区别在于指数位和尾数位的分配策略不同：

选择建议：如果硬件支持 BF16，优先使用 BF16。它的数值范围与 FP32 完全相同，训练过程中几乎不会出现溢出问题，且不需要 GradScaler。


## 实例


## 3. 进阶技巧与优化


### 3.1 动态损失缩放

GradScaler 的核心机制是动态损失缩放——它会根据训练状态自动调整缩放因子，既能防止梯度下溢，又能在训练稳定时逐步降低缩放以减少精度损失：

GradScaler 自动管理上述反馈循环，你只需通过参数微调其行为：


## 实例


### 3.2 梯度累积中的 AMP

梯度累积用于在有限显存下模拟更大的 batch size。使用 AMP 时，需要注意每个子 batch 的 loss 必须除以累积步数，否则最终梯度会被放大：


## 实例


### 3.3 验证与推理中的 AMP

验证和推理阶段同样推荐使用 AMP。由于不需要反向传播和梯度缩放，代码更加简洁：


## 实例


## 4. 常见问题与解决方案


### 4.1 训练不稳定


### 4.2 手动控制精度

某些操作在 FP16 下精度损失较大，需要手动指定使用 FP32。PyTorch 的 autocast 已经内置了对这些操作的保护，但自定义操作可能需要手动处理：


## 实例

提示：PyTorch 的 autocast 会自动将以下操作保持在 FP32：softmax、log_softmax、cross_entropy、layer_norm、batch_norm 等。通常只有自定义算子才需要手动处理。


### 4.3 梯度裁剪与 AMP

梯度裁剪必须在 scaler.step() 之前、且在 scaler.unscale_() 之后执行。这是因为裁剪需要作用在真实梯度值上，而非缩放后的梯度：


## 实例


## 5. 性能对比与最佳实践


## 后续章节

- 5.1 性能基准测试
- 实例
- 5.2 显存对比
- 实例
- 5.3 最佳实践总结
- 6. 与其他优化技术的结合
- 6.1 AMP + torch.compile
- 实例
- 6.2 AMP + 分布式训练
- 实例
- 总结

## 复习重点

- 能说明 `PyTorch 混合精度训练` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
