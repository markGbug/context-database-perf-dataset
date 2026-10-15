# AI Agent（智能体）：Hugging Face Transformers

- 来源：[Hugging Face Transformers](https://www.runoob.com/ai-agent/hugging-face-transformers.html)
- 分类：AI / 智能开发
- 技术：AI Agent（智能体）
- 笔记类型：概念卡
- 章节序号：0048

## 本章内容

Hugging Face Transformers 是目前最流行的开源 NLP / AI 库，提供数千个预训练模型，覆盖文本、图像、音频、多模态等几乎所有 AI 任务。

它的核心价值：把复杂的模型加载、推理、训练流程封装成几行代码。


### 支持的任务类型


## Transformer 架构核心原理

在使用库之前，理解底层架构会让你知道为什么这样调参。


### 整体架构：Encoder-Decoder


### 三大模型家族


## 安装与环境配置


### 安装

```text
# 基础安装
pip install transformers

# 完整安装（包含训练依赖）
pip install transformers[torch]       # PyTorch 后端（推荐）
pip install transformers[tf-cpu]      # TensorFlow 后端
pip install transformers[flax]        # JAX/Flax 后端

# 常用配套库
pip install datasets          # HuggingFace 数据集库
pip install evaluate          # 模型评估指标
pip install accelerate        # 多GPU/混合精度训练
pip install peft              # 参数高效微调（LoRA等）
pip install tokenizers        # 高性能分词器
pip install sentencepiece     # 部分模型（T5/LLaMA）需要

# 验证安装
python -c "import transformers; print(transformers.__version__)"
```


### 环境变量配置

```text
# 设置模型缓存目录（模型下载后缓存到此路径，默认 ~/.cache/huggingface）
export HF_HOME=/data/huggingface_cache

# 国内用户：使用镜像站加速下载（推荐 hf-mirror.com）
export HF_ENDPOINT=https://hf-mirror.com

# 离线模式（网络不可用时，只使用已缓存的模型）
export TRANSFORMERS_OFFLINE=1

# 禁用进度条（CI/CD 环境）
export DISABLE_TQDM=1
```


## 实例


## Pipeline：五行代码跑 AI

Pipeline 是 Transformers 最高级别的抽象，把模型加载、预处理、推理、后处理全部封装好，三到五行代码即可完成推理。


### Pipeline 快速示例大全


## 实例


### Pipeline 进阶配置


## 实例


## Tokenizer 深度解析

Tokenizer 是 NLP 的第一步：把原始文本转换成模型能理解的数字序列。


### Tokenization 完整流程


### Tokenizer 核心用法


## 实例


### 常见 Tokenizer 类型对比


## 模型加载与推理


### AutoClass：自动选择正确的模型类


## 实例


### 提取句子向量


## 实例


## 十大常见任务实战


## 后续章节

- 文本分类（情感分析）
- 实例
- 文本生成（对话 / 续写）
- 实例
- 命名实体识别（NER）
- 实例
- 机器翻译
- 实例
- 文本摘要
- 实例
- 微调（Fine-tuning）
- 微调流程全景
- 完整微调示例：文本分类
- 实例
- LoRA 参数高效微调（推荐）
- 实例

## 记忆卡片

- 一句话定义：`Hugging Face Transformers` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
