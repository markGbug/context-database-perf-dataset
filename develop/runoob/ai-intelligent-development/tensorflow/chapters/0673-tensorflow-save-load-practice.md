# TensorFlow：TensorFlow 模型保存与加载

- 来源：[TensorFlow 模型保存与加载](https://www.runoob.com/tensorflow/tensorflow-save-load.html)
- 分类：AI / 智能开发
- 技术：TensorFlow
- 笔记类型：练习笔记
- 章节序号：0673

## 本章内容

在机器学习和深度学习项目中，模型的保存与加载是至关重要的环节。

TensorFlow 提供了多种方式来保存和恢复模型，使开发者能够：

- 保存训练好的模型供后续使用
- 分享模型给其他开发者
- 从检查点恢复训练
- 部署模型到生产环境

TensorFlow 2.x 主要支持三种模型保存格式：

- SavedModel 格式（推荐）
- HDF5 格式（.h5）
- 旧版 Keras 格式


## 保存整个模型


### SavedModel 格式

SavedModel 是 TensorFlow 推荐的模型保存格式，它包含完整的模型信息：


## 实例

保存后的目录结构：

```text
my_model/
├── assets/
├── variables/
│   ├── variables.data-00000-of-00001
│   └── variables.index
└── saved_model.pb
```


### HDF5 格式

HDF5 是另一种常用的模型保存格式：


## 实例


### 两种格式的区别


## 加载整个模型


### 从 SavedModel 加载


## 实例


### 从 HDF5 文件加载


## 实例


## 选择性保存与加载


### 仅保存权重


## 实例


### 加载权重


## 实例


### 保存自定义训练循环的检查点


## 实例


## 模型保存与加载的最佳实践

- 生产环境部署：优先使用 SavedModel 格式
- 跨平台共享：HDF5 格式更通用
- 训练中断恢复：使用检查点回调定期保存
- 自定义对象处理： model.save('custom_model', save_format='tf')
- 模型版本控制：为不同版本的模型创建不同目录


## 常见问题与解决方案


### 自定义层/模型保存问题


## 实例


### 跨版本兼容性问题

- 尽量使用相同版本的 TensorFlow 保存和加载模型
- 对于生产环境，考虑使用 TensorFlow Serving 来避免版本问题


### 大模型保存优化


## 后续章节

- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `TensorFlow 模型保存与加载` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
