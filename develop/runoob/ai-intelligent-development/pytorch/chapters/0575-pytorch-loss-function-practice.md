# PyTorch：PyTorch 损失函数

- 来源：[PyTorch 损失函数](https://www.runoob.com/pytorch/pytorch-loss-function.html)
- 分类：AI / 智能开发
- 技术：PyTorch
- 笔记类型：练习笔记
- 章节序号：0575

## 本章内容

损失函数（Loss Function）衡量模型预测值与真实值之间的差距，是神经网络训练的核心指引——优化器通过最小化损失函数来更新模型参数。

PyTorch 在 torch.nn 模块中内置了十余种常用损失函数，覆盖分类、回归、排序等主要任务类型。


## 1. 损失函数基础


### 基本用法

所有 PyTorch 损失函数都是 nn.Module 的子类，使用方式统一：


## 实例


### 预测值的形态约定

不同损失函数对输入的形态要求不同，这是初学者最容易出错的地方：

N = batch size，C = 类别数


## 2. 分类任务损失函数


### 2.1 CrossEntropyLoss 交叉熵损失

最常用的多分类损失函数，内部自动执行 Softmax + 对数 + 负号，无需手动对模型输出做 Softmax。

数学公式：

Loss = -sum(y_c * log(p_c))

其中 p_c = exp(x_c) / sum_j exp(x_j) 是 Softmax 输出。


## 实例

支持软标签（Label Smoothing）：


## 实例

适用场景：多分类（猫/狗/鸟）、图像分类、文本分类等所有多分类任务。


### 2.2 BCELoss 二元交叉熵损失

专用于二分类或多标签分类任务，输入必须是经过 Sigmoid 处理后的概率值（0~1）。

数学公式：

Loss = -[y * log(p) + (1-y) * log(1-p)]


## 实例

BCELoss 要求输入在 (0, 1) 范围内，传入原始 logits 会导致数值不稳定甚至 NaN。推荐使用下方的 BCEWithLogitsLoss。


### 2.3 BCEWithLogitsLoss

BCELoss 的改进版，内部自动执行 Sigmoid，数值更稳定，推荐优先使用。


## 实例

带正样本权重（处理类别不平衡）：


## 实例

适用场景：二分类（垃圾邮件判断）、多标签分类（文章多标签打标）、目标检测（前景/背景判断）。


### 2.4 NLLLoss 负对数似然损失

需要手动对模型输出做 log_softmax，灵活性更高。CrossEntropyLoss = LogSoftmax + NLLLoss。


## 实例

使用场景：需要在中间步骤使用 log 概率时（如 CTC、Beam Search）；其他情况优先用 CrossEntropyLoss。


## 3. 回归任务损失函数


### 3.1 MSELoss 均方误差

最经典的回归损失，对大误差非常敏感（因为平方会放大大误差的影响）。

数学公式：

MSELoss = (1/N) * sum((y_i - y_hat_i)^2)


## 实例

适用场景：房价预测、温度预测等连续值回归，数据中没有明显离群点时效果好。


### 3.2 L1Loss 平均绝对误差

对离群点（outlier）更鲁棒，因为取绝对值而非平方，大误差不会被过度放大。

数学公式：

L1Loss = (1/N) * sum(|y_i - y_hat_i|)


## 实例


### 3.3 SmoothL1Loss Huber 损失

融合 MSE 和 L1 的优点：误差小时用 MSE（平滑，梯度稳定），误差大时用 L1（抗离群点）。目标检测（Faster R-CNN）中的标准损失。

数学公式：

SmoothL1(x) = 0.5*x^2 if |x| < 1, else |x| - 0.5


## 实例

三种回归损失对比：


## 实例

```text
输出示例：
MSELoss     : ['0.00', '1.00', '25.00', '100.00']   # 大误差被平方放大
L1Loss      : ['0.00', '1.00',  '5.00',  '10.00']   # 线性增长
SmoothL1    : ['0.00', '0.50',  '4.50',   '9.50']   # 中间值
```

适用场景：目标检测的边框回归、深度估计等，同时存在小误差和离群点的回归任务。


## 4. 进阶损失函数


## 后续章节

- 4.1 HuberLoss
- 实例
- 4.2 KLDivLoss KL 散度
- 实例
- 实例
- 4.3 MarginRankingLoss 排序损失
- 实例
- 4.4 TripletMarginLoss 三元组损失
- 实例
- 4.5 CTCLoss 序列标注损失
- 实例
- 5. reduction 参数详解
- 实例
- 实例
- 6. 类别权重与样本权重
- 类别权重（处理类别不平衡）

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PyTorch 损失函数` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
