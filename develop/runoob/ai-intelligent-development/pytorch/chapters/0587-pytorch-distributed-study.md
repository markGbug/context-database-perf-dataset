# PyTorch：PyTorch 分布式训练

- 来源：[PyTorch 分布式训练](https://www.runoob.com/pytorch/pytorch-distributed.html)
- 分类：AI / 智能开发
- 技术：PyTorch
- 笔记类型：学习笔记
- 章节序号：0587

## 本章内容

当模型越来越大、数据越来越多时，单 GPU 已经无法满足训练需求。

分布式训练通过多 GPU 甚至多台机器并行计算，可以显著缩短训练时间。

本节详细介绍 PyTorch 中的分布式训练技术，包括 DataParallel、DistributedDataParallel 以及混合精度分布式训练。


## 1. 分布式训练基础


### 1.1 为什么需要分布式训练

深度学习模型的规模逐年增长，训练时间也随之增加。分布式训练的核心目标是：将计算任务分散到多个计算单元上，在可接受的时间内完成大规模模型和数据的训练。

分布式训练主要解决两个问题：

- 显存不足：大模型的参数、优化器状态、梯度需要大量显存
- 训练时间过长：单 GPU 训练大模型可能需要数周甚至数月


### 1.2 分布式训练的两大模式

分布式训练主要分为两种模式：

实际生产环境中，数据并行是最常用的方式。PyTorch 提供了 DataParallel 和 DistributedDataParallel 两种实现。


## 2. DataParallel 使用指南


### 2.1 单机多卡：DataParallel

DataParallel（DP） 是 PyTorch 提供的最简便的多 GPU 训练方式。它只需要修改几行代码，就可以利用单机上的多个 GPU 进行训练。


## 实例


### 2.2 DataParallel 的工作原理

DataParallel 的工作流程如下：

- 模型复制：将模型复制到每个 GPU 上
- 数据分发：将 batch 数据均匀分配到各个 GPU
- 并行计算：每个 GPU 独立计算前向传播
- 梯度聚合：将所有 GPU 的梯度汇总到主 GPU
- 参数更新：主 GPU 更新参数后同步到其他 GPU


## 实例

DataParallel 简单易用，但存在两个主要问题：1）主 GPU 显存压力大（需要汇总梯度）；2）GPU 之间的通信效率较低。因此，官方推荐使用 DistributedDataParallel。


## 3. DistributedDataParallel 详解


### 3.1 DDP 基础

DistributedDataParallel（DDP） 是 PyTorch 推荐的分布式训练方式。相比 DataParallel，DDP 具有以下优势：

- 每个 GPU 独立计算梯度，无需在主 GPU 汇总
- 使用高效的梯度同步算法（Ring AllReduce）
- 支持多机多卡训练
- 训练速度更快，显存利用更高效


### 3.2 DDP 单机多卡训练


## 实例


### 3.3 启动分布式训练

PyTorch 分布式训练需要通过 torchrun 或 torch.distributed.launch 启动。以下是常用的启动方式：


## 实例


### 3.4 完整的 DDP 训练脚本


## 实例

关键点：每个 epoch 都需要调用 sampler.set_epoch(epoch)，确保数据划分被打乱，否则多个进程会看到相同的数据。


## 4. 分布式训练中的混合精度


### 4.1 DDP + AMP 组合

分布式训练与混合精度训练结合，可以进一步提升训练速度。PyTorch 2.0+ 的 DDP 已经与 AMP 完美集成。


## 实例


### 4.2 分布式训练中的梯度同步

DDP 使用 Ring AllReduce 算法进行梯度同步，其工作原理如下：

- 每个 GPU 将梯度分为 n 份（n 为 GPU 数量）
- 每个 GPU 与相邻 GPU 交换一份梯度
- 重复 n 次后，每个 GPU 拥有完整的梯度


## 实例


## 5. 模型并行与流水线


### 5.1 简单的模型并行

当模型太大，单个 GPU 无法容纳时，需要将模型拆分到多个 GPU 上。


## 实例


## 后续章节

- 5.2 流水线并行（Pipeline Parallelism）
- 实例
- 6. 分布式训练最佳实践
- 6.1 性能优化技巧
- 6.2 常见问题与解决方案
- 6.3 完整的多机多卡训练脚本
- 实例
- 7. 分布式训练监控与调试
- 7.1 常用监控工具
- 实例
- 7.2 调试技巧

## 复习重点

- 能说明 `PyTorch 分布式训练` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
