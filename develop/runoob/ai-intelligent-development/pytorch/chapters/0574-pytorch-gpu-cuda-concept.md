# PyTorch：PyTorch GPU / CUDA 加速

- 来源：[PyTorch GPU / CUDA 加速](https://www.runoob.com/pytorch/pytorch-gpu-cuda.html)
- 分类：AI / 智能开发
- 技术：PyTorch
- 笔记类型：概念卡
- 章节序号：0574

## 本章内容

深度学习的核心操作是大规模矩阵乘法与元素运算。CPU 的设计目标是处理复杂的串行逻辑，核心数通常为 8~64 个；而 GPU 拥有数千个简单并行核心，天然适合这类高度并行的数值计算。PyTorch 通过 NVIDIA 的 CUDA（Compute Unified Device Architecture）框架调用 GPU，可将训练速度提升数十倍乃至百倍。


## 1. CPU 与 GPU 的差异

GPU 训练速度的提升主要来自两方面：其一是并行执行大量相同计算；其二是高带宽显存使得数据搬运速度远快于 CPU 内存。

对于矩阵乘法这类运算密集型操作，加速效果尤为显著。

如果使用 Apple Silicon（M1/M2/M3），PyTorch 通过 mps 后端支持 Metal GPU 加速，用法与 CUDA 几乎完全相同，只需将设备改为 "mps"。


## 2. 检测 CUDA 环境

使用 GPU 前，需要先确认当前环境是否安装了支持 CUDA 的 PyTorch。

同时需要检查系统上是否存在可用的 GPU 设备。


## 实例

输出示例：

```text
CUDA 可用: True
GPU 数量: 1
当前 GPU: 0
GPU 型号: NVIDIA GeForce RTX 4090
PyTorch 版本: 2.3.0+cu121
CUDA 版本: 12.1
```


### 2.1 动态选择设备（推荐写法）

在代码中硬编码 "cuda" 会导致没有 GPU 的机器直接报错。


## 实例


## 3. 张量在设备间移动

PyTorch 中的张量默认在 CPU 上创建。

要使用 GPU 计算，需要显式将张量移动到 GPU，或直接在 GPU 上创建。


### 3.1 基本移动方法


## 实例

GPU 张量转 numpy 时，必须先移回 CPU，且若张量附带梯度还需先 detach：


## 实例


### 3.2 设备一致性约束

不同设备上的张量不能直接参与同一运算。

否则会抛出 RuntimeError：


## 实例

查看张量所在设备：


## 实例


### 3.3 速度对比验证


## 实例

输出示例：

```text
CPU 耗时: 1.847s
GPU 耗时: 0.021s
```

GPU 计算是异步执行的——Python 调用返回后，GPU 上的运算可能尚未完成。计时时必须调用 torch.cuda.synchronize() 等待 GPU 真正结束，否则测量结果不准确。


## 4. 模型移动到 GPU

模型的所有参数（weight、bias）本质上也是张量。

这些参数同样需要移动到 GPU 才能在 GPU 上执行前向传播和反向传播。

对整个模型调用 .to(device) 即可，PyTorch 会自动遍历并移动所有内部参数。


## 实例

模型在 GPU 上，但输入数据仍在 CPU 上时，前向传播会报错。务必在 DataLoader 读取每个 batch 之后，将 inputs 和 labels 都调用 .to(device)。


## 5. 完整训练流程

以下是一个包含数据加载、模型训练、验证评估的标准 GPU 训练模板。


## 实例

关键要点：

- device 变量在代码最顶部声明，全局统一引用，不硬编码 "cuda"
- 模型 .to(device) 只需调用一次
- 每个 batch 的 inputs 和 labels 都要 .to(device)
- DataLoader 设置 pin_memory=True 和 non_blocking=True 加速数据传输
- 验证阶段使用 torch.no_grad() 关闭梯度，节省显存


## 6. 多 GPU 训练

当单卡显存不足时，可以考虑使用多 GPU 并行训练。

此外，多 GPU 还能进一步提升训练速度。PyTorch 提供了两种主要方式。


### 6.1 DataParallel

这是最简单的多卡方式。

它采用单进程，将每个 batch 均分到各 GPU，前向传播并行执行，梯度在主卡上汇总更新。使用方便，但主卡负担重，多卡利用率不均衡，适合快速入门。


## 实例

如果需要访问原始模型的属性（如自定义方法），需要通过 .module 访问：


## 实例


### 6.2 DistributedDataParallel

这是多进程方式。

每个进程绑定一块 GPU，每张卡持有完整模型，通过 All-Reduce 同步梯度。是生产环境和大规模训练的推荐方案，效率远高于 DataParallel。


## 实例


## 后续章节

- 7. 混合精度训练 AMP
- 实例
- 7.1 FP16 与 BF16 的选择
- 实例
- 8. 性能优化技巧
- 8.1 显存管理
- 实例
- 8.2 DataLoader 优化
- 实例
- 8.3 torch.compile 模型编译（PyTorch 2.0+）
- 实例
- 8.4 梯度累积（模拟大 batch）
- 实例
- 8.5 显存不足时的应对策略
- 9. 常见错误与排查
- 9.1 RuntimeError: Expected all tensors to be on the same device

## 记忆卡片

- 一句话定义：`PyTorch GPU / CUDA 加速` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
