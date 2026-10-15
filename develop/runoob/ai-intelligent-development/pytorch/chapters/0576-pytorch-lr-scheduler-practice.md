# PyTorch：PyTorch 学习率调度器

- 来源：[PyTorch 学习率调度器](https://www.runoob.com/pytorch/pytorch-lr-scheduler.html)
- 分类：AI / 智能开发
- 技术：PyTorch
- 笔记类型：练习笔记
- 章节序号：0576

## 本章内容

学习率（Learning Rate）是神经网络训练中最重要的超参数之一。学习率过大，训练震荡甚至发散；学习率过小，收敛极慢，容易陷入局部最优。

学习率调度器（LR Scheduler） 通过在训练过程中动态调整学习率，兼顾训练初期的快速收敛与后期的精细调优。


## 1. 基础概念与使用模式


### 标准使用流程


## 实例


### step() 的调用时机


## 实例

注意：optimizer.step() 必须在 scheduler.step() 之前调用。


### 查看和保存学习率状态


## 实例


## 2. 固定衰减调度器


### 2.1 StepLR 按步衰减

每隔固定 step_size 个 epoch，将学习率乘以 gamma。是最简单、最常用的调度器之一。

公式： lr = lr_base * gamma^(floor(step / step_size))


## 实例

适用场景：训练节奏固定、阶段清晰的任务，如 ResNet 在 ImageNet 上的训练（90 epoch，在第 30、60 epoch 衰减）。


### 2.2 MultiStepLR 多里程碑衰减

在指定的若干个 epoch（里程碑）处衰减学习率，比 StepLR 更灵活。


## 实例

适用场景：已知在哪些 epoch 模型需要精细调整，如分类模型中后期精细收敛阶段。


### 2.3 ExponentialLR 指数衰减

每个 epoch 都衰减，学习率以指数形式持续下降，衰减更平滑。

公式： lr = lr_base * gamma^epoch


## 实例

gamma 设置得太小（如 0.5）会导致学习率迅速趋近于零，通常设在 0.9~0.99 之间。


## 3. 自适应调度器


### 3.1 ReduceLROnPlateau 监控指标衰减

最智能的调度器之一：监控某个指标（如验证集 loss），当该指标停止改善时自动降低学习率。不需要提前知道在哪个 epoch 衰减。


## 实例

监控 Accuracy 的写法：


## 实例

适用场景：几乎所有任务的默认首选，尤其是不确定训练多少 epoch、或训练不稳定时。


### 3.2 CosineAnnealingLR 余弦退火

学习率按余弦曲线从初始值平滑下降到最小值（eta_min），避免了阶梯式衰减的突变。

公式： lr_t = eta_min + 0.5 * (eta_max - eta_min) * (1 + cos(t * pi / T_max)


## 实例

适用场景：训练 epoch 数固定的场景，在 Vision Transformer、ResNet 等论文中广泛使用，收敛质量好。


### 3.3 CosineAnnealingWarmRestarts

余弦退火的升级版，支持周期性重启（Warm Restarts）：每个周期结束后学习率重置回初始值，开始新一轮余弦衰减。允许模型跳出局部最优。


## 实例

适用场景：训练大模型、或希望模型从多个收敛点中选最优时，配合 Snapshot Ensemble 使用效果显著。


## 4. 预热调度器

Warmup（预热）是指训练开始的若干步内，学习率从一个极小值逐渐升高到目标值。大 batch size 训练、Transformer 类模型几乎都需要预热，否则初期梯度更新过猛，模型难以稳定。


### 4.1 LinearLR 线性调度

在指定 epoch 内线性改变学习率（可用于线性预热或线性衰减）。


## 后续章节

- 实例
- 4.2 ConstantLR 常数阶段
- 实例
- 4.3 SequentialLR 组合调度
- 实例
- 5. 循环调度器
- 5.1 CyclicLR 循环学习率
- 实例
- 5.2 OneCycleLR 单周期策略
- 实例
- 6. 自定义调度器
- 6.1 LambdaLR 函数式自定义
- 实例
- 6.2 继承 LRScheduler
- 实例
- 7. 调度器可视化对比

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PyTorch 学习率调度器` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
