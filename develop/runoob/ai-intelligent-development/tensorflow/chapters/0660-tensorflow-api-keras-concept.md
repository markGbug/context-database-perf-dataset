# TensorFlow：TensorFlow 高级 API - Keras

- 来源：[TensorFlow Keras](https://www.runoob.com/tensorflow/tensorflow-api-keras.html)
- 分类：AI / 智能开发
- 技术：TensorFlow
- 笔记类型：概念卡
- 章节序号：0660

## 本章内容

Keras 是一个用 Python 编写的高级神经网络 API，它能够以 TensorFlow, CNTK 或 Theano 作为后端运行。Keras 的设计理念是用户友好、模块化和易扩展。


### Keras 的主要特点

- 简单易用：提供直观一致的接口，适合快速原型设计
- 模块化：神经网络层、损失函数、优化器等都是可插拔的模块
- 易扩展：可以轻松添加新模块来表达新的研究想法
- 支持多后端：可以无缝运行在 TensorFlow, CNTK 或 Theano 上


## Keras 核心概念


### 1. 模型 (Model)

Keras 的核心数据结构是模型，模型是组织神经网络层的方式。Keras 提供了两种主要的模型：

- Sequential 模型：层的线性堆叠
- Functional API：构建复杂模型的有向无环图


### 2. 层 (Layer)

层是 Keras 的基本构建块，每个层接收输入数据，进行某种计算后输出结果。Keras 提供了多种预定义层：

- 核心层：Dense, Activation, Dropout 等
- 卷积层：Conv2D, MaxPooling2D 等
- 循环层：LSTM, GRU 等
- 其他：Embedding, BatchNormalization 等


### 3. 激活函数 (Activation Function)

激活函数决定神经元的输出，常用的有：

- ReLU (Rectified Linear Unit)
- Sigmoid
- Tanh
- Softmax (多分类问题)


## Keras 基本工作流程


### 1. 定义模型


## 实例


### 2. 编译模型


## 实例


### 3. 训练模型


## 实例


### 4. 评估模型


## 实例


### 5. 进行预测


## 实例


## Keras 常用层详解


### 1. Dense 全连接层


## 实例

- units：正整数，输出空间的维度
- activation：激活函数
- use_bias：是否使用偏置向量
- kernel_initializer：权重矩阵的初始化器
- bias_initializer：偏置向量的初始化器


### 2. Conv2D 二维卷积层


## 实例

- filters：卷积核的数目
- kernel_size：卷积核的尺寸
- strides：卷积步长
- padding：填充方式 ('valid' 或 'same')


### 3. LSTM 长短期记忆网络层


## 实例

- units：正整数，输出空间的维度
- activation：激活函数
- recurrent_activation：循环步的激活函数
- return_sequences：是否返回完整序列


## Keras 模型保存与加载


## 后续章节

- 1. 保存整个模型
- 实例
- 2. 仅保存架构
- 实例
- 3. 仅保存权重
- 实例
- 4. 加载模型
- 实例
- Keras 回调函数
- 常用回调函数
- 实例
- Keras 实践示例：MNIST 手写数字识别
- 实例
- Keras 进阶技巧
- 1. 自定义层
- 实例

## 记忆卡片

- 一句话定义：`TensorFlow Keras` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
