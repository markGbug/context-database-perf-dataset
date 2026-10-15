# PyTorch：PyTorch 数据转换

- 来源：[PyTorch 数据转换](https://www.runoob.com/pytorch/pytorch-transforms.html)
- 分类：AI / 智能开发
- 技术：PyTorch
- 笔记类型：学习笔记
- 章节序号：0562

## 本章内容

在 PyTorch 中，数据转换（Data Transformation） 是一种在加载数据时对数据进行处理的机制，将原始数据转换成适合模型训练的格式，主要通过 torchvision.transforms 提供的工具完成。

数据转换不仅可以实现基本的数据预处理（如归一化、大小调整等），还能帮助进行数据增强（如随机裁剪、翻转等），提高模型的泛化能力。


### 为什么需要数据转换？

数据预处理：

- 调整数据格式、大小和范围，使其适合模型输入。
- 例如，图像需要调整为固定大小、张量格式并归一化到 [0,1]。

数据增强：

- 在训练时对数据进行变换，以增加多样性。
- 例如，通过随机旋转、翻转和裁剪增加数据样本的变种，避免过拟合。

灵活性：

- 通过定义一系列转换操作，可以动态地对数据进行处理，简化数据加载的复杂度。

在 PyTorch 中，torchvision.transforms 模块提供了多种用于图像处理的变换操作。


### 基础变换操作

1、ToTensor

将 PIL 图像或 NumPy 数组转换为 PyTorch 张量。

同时将像素值从 [0, 255] 归一化为 [0, 1]。

```text
from torchvision import transforms

transform = transforms.ToTensor()
```

2、Normalize

对数据进行标准化，使其符合特定的均值和标准差。

通常用于图像数据，将其像素值归一化为零均值和单位方差。

```text
transform = transforms.Normalize(mean=[0.5], std=[0.5])  # 归一化到 [-1, 1]
```

3、Resize

调整图像的大小。

```text
transform = transforms.Resize((128, 128))  # 将图像调整为 128x128
```

4、CenterCrop

从图像中心裁剪指定大小的区域。

```text
transform = transforms.CenterCrop(128)  # 裁剪 128x128 的区域
```


### 数据增强操作

1、RandomCrop

从图像中随机裁剪指定大小。

```text
transform = transforms.RandomCrop(128)
```

2、RandomHorizontalFlip

以一定概率水平翻转图像。

```text
transform = transforms.RandomHorizontalFlip(p=0.5)  # 50% 概率翻转
```

3、RandomRotation

随机旋转一定角度。

```text
transform = transforms.RandomRotation(degrees=30)  # 随机旋转 -30 到 +30 度
```

4、ColorJitter

随机改变图像的亮度、对比度、饱和度或色调。

```text
transform = transforms.ColorJitter(brightness=0.5, contrast=0.5)
```


### 组合变换

通过 transforms.Compose 将多个变换组合起来。

```text
transform = transforms.Compose([
    transforms.Resize((128, 128)),
    transforms.RandomHorizontalFlip(p=0.5),
    transforms.ToTensor(),
    transforms.Normalize(mean=[0.5], std=[0.5])
])
```


### 自定义转换

如果 transforms 提供的功能无法满足需求，可以通过自定义类或函数实现。


## 实例


## 实例


### 对图像数据集应用转换

加载 MNIST 数据集，并应用转换。


## 实例

输出结果为：

```text
图像张量大小: torch.Size([32, 1, 128, 128])
```


### 可视化转换效果

以下代码展示了原始数据和经过转换后的数据对比。


## 实例

显示如下所示：


## 复习重点

- 能说明 `PyTorch 数据转换` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
