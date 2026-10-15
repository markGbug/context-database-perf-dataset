# PyTorch：PyTorch TorchScript / ONNX 导出

- 来源：[PyTorch TorchScript/ONNX 导出](https://www.runoob.com/pytorch/pytorch-torchscript-onnx-export.html)
- 分类：AI / 智能开发
- 技术：PyTorch
- 笔记类型：练习笔记
- 章节序号：0586

## 本章内容

模型训练完成后，需要将模型部署到生产环境。PyTorch 提供了多种模型导出方式，其中 TorchScript 和 ONNX 是最常用的两种格式。

本节详细介绍这两种导出方式的原理、使用方法和最佳实践。

模型导出是将 PyTorch 模型转换为可以在不同平台、不同框架上运行的格式的过程。这对于模型部署、移动端推理、跨框架迁移等场景至关重要。


## 1. TorchScript 基础


### 1.1 什么是 TorchScript

TorchScript 是 PyTorch 的序列化格式，它可以将 Python 代码转换为可以独立运行的 C++ 虚拟机代码。TorchScript 程序可以在没有 Python 解释器的环境中运行。

TorchScript 的主要特点：

- 将动态图转换为静态图
- 支持 Python 子集的语法
- 可以在 C++ 环境中运行
- 保留模型的结构和参数


### 1.2 两种转换方式

TorchScript 提供两种将模型转换为 TorchScript 的方式：

- TorchScript 追踪（Tracing）：通过执行模型记录操作，生成静态计算图
- TorchScript 脚本（Scripting）：直接分析 Python 代码，编译为 TorchScript


## 2. TorchScript 追踪 (Tracing)


### 2.1 基本追踪方法


## 实例


### 2.2 追踪的限制

追踪方法有一些限制：

- 只记录实际执行的操作
- 控制流（如 if、for）会被固定
- 动态大小的输入可能有问题


## 实例

对于包含控制流的模型，应该使用 TorchScript 脚本（Scripting）而不是追踪。


## 3. TorchScript 脚本 (Scripting)


### 3.1 基本使用方法


## 实例


### 3.2 复杂模型的脚本化


## 实例


## 4. ONNX 导出


### 4.1 ONNX 基础

ONNX（Open Neural Network eXchange） 是一个开放的神经网络交换格式，支持在不同的深度学习框架之间转换模型。

ONNX 的优势：

- 跨框架：PyTorch、TensorFlow、Caffe2 等都支持
- 跨平台：支持 CPU、GPU、移动端等多种平台
- 硬件优化：可利用 ONNX Runtime 进行高效推理
- 工具丰富：有大量的优化工具和部署方案


### 4.2 基本 ONNX 导出


## 实例


### 4.3 导出复杂模型


## 实例


## 5. 导出的验证与优化


### 5.1 验证导出模型


## 实例


### 5.2 ONNX Runtime 优化


## 实例


## 后续章节

- 5.3 模型量化
- 实例
- 6. 移动端部署
- 6.1 导出到移动端格式
- 实例
- 6.2 Core ML 导出（iOS）
- 实例
- 7. 最佳实践与常见问题
- 7.1 导出问题排查
- 7.2 导出格式对比
- 7.3 导出检查清单
- 实例
- 7.4 完整导出流程
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PyTorch TorchScript/ONNX 导出` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
