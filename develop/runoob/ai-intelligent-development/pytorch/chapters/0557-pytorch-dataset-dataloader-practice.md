# PyTorch：PyTorch 数据处理与加载

- 来源：[PyTorch 数据处理与加载](https://www.runoob.com/pytorch/pytorch-dataset-dataloader.html)
- 分类：AI / 智能开发
- 技术：PyTorch
- 笔记类型：练习笔记
- 章节序号：0557

## 本章内容

在 PyTorch 中，处理和加载数据是深度学习训练过程中的关键步骤。

为了高效地处理数据，PyTorch 提供了强大的工具，包括 torch.utils.data.Dataset 和 torch.utils.data.DataLoader，帮助我们管理数据集、批量加载和数据增强等任务。

PyTorch 数据处理与加载的介绍：

- 自定义 Dataset：通过继承 torch.utils.data.Dataset 来加载自己的数据集。
- DataLoader：DataLoader 按批次加载数据，支持多线程加载并进行数据打乱。
- 数据预处理与增强：使用 torchvision.transforms 进行常见的图像预处理和增强操作，提高模型的泛化能力。
- 加载标准数据集：torchvision.datasets 提供了许多常见的数据集，简化了数据加载过程。
- 多个数据源：通过组合多个 Dataset 实例来处理来自不同来源的数据。


## 自定义 Dataset

torch.utils.data.Dataset 是一个抽象类，允许你从自己的数据源中创建数据集。

我们需要继承该类并实现以下两个方法：

- __len__(self)：返回数据集中的样本数量。
- __getitem__(self, idx)：通过索引返回一个样本。

假设我们有一个简单的 CSV 文件或一些列表数据，我们可以通过继承 Dataset 类来创建自己的数据集。


## 实例


## 使用 DataLoader 加载数据

DataLoader 是 PyTorch 提供的一个重要工具，用于从 Dataset 中按批次（batch）加载数据。

DataLoader 允许我们批量读取数据并进行多线程加载，从而提高训练效率。


## 实例

- batch_size: 每次加载的样本数量。
- shuffle: 是否对数据进行洗牌，通常训练时需要将数据打乱。
- drop_last: 如果数据集中的样本数不能被 batch_size 整除，设置为 True 时，丢弃最后一个不完整的 batch。

输出：

```text
Batch 1:
Inputs: tensor([[3., 4.], [1., 2.]])
Labels: tensor([0., 1.])
Batch 2:
Inputs: tensor([[7., 8.], [5., 6.]])
Labels: tensor([0., 1.])
```

每次循环中，DataLoader 会返回一个批次的数据，包括输入特征（inputs）和目标标签（labels）。


## 预处理与数据增强

数据预处理和增强对于提高模型的性能至关重要。

PyTorch 提供了 torchvision.transforms 模块来进行常见的图像预处理和增强操作，如旋转、裁剪、归一化等。

常见的图像预处理操作:


## 实例

- transforms.Compose()：将多个变换操作组合在一起。
- transforms.Resize()：调整图像大小。
- transforms.ToTensor()：将图像转换为 PyTorch 张量，值会被归一化到 [0, 1] 范围。
- transforms.Normalize()：标准化图像数据，通常使用预训练模型时需要进行标准化处理。


### 图像数据增强

数据增强技术通过对训练数据进行随机变换，增加数据的多样性，帮助模型更好地泛化。例如，随机翻转、旋转、裁剪等。


## 实例

这些数据增强方法可以通过 transforms.Compose() 组合使用，保证每个图像在训练时具有不同的变换。


## 加载图像数据集

对于图像数据集，torchvision.datasets 提供了许多常见数据集（如 CIFAR-10、ImageNet、MNIST 等）以及用于加载图像数据的工具。

加载 MNIST 数据集:


## 实例

- datasets.MNIST() 会自动下载 MNIST 数据集并加载。
- transform 参数允许我们对数据进行预处理。
- train=True 和 train=False 分别表示训练集和测试集。


## 用多个数据源（Multi-source Dataset）

如果你的数据集由多个文件、多个来源（例如多个图像文件夹）组成，可以通过继承 Dataset 类自定义加载多个数据源。

PyTorch 提供了 ConcatDataset 和 ChainDataset 等类来连接多个数据集。

例如，假设我们有多个图像文件夹的数据，可以将它们合并为一个数据集：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PyTorch 数据处理与加载` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
