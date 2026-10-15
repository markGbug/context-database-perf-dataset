# AI Agent（智能体）：GraphRAG 入门教程

- 来源：[GraphRAG 入门教程](https://www.runoob.com/ai-agent/graphrag-usage.html)
- 分类：AI / 智能开发
- 技术：AI Agent（智能体）
- 笔记类型：学习笔记
- 章节序号：0026

## 本章内容

GraphRAG 是微软研究院开源的一种结构化、层次化的检索增强生成（RAG）系统，与传统 RAG 使用纯文本向量检索不同，GraphRAG 先用大模型从原始文档中抽取出实体和关系，构建知识图谱，再基于图结构进行检索和问答。

本教程面向零基础读者，带你从安装开始，完整走完 文档 → 知识图谱 → 查询问答 的全流程，模型使用 qwen-plus，Embedding 使用阿里云通义的 text-embedding-v4。


## 什么是 GraphRAG

要理解 GraphRAG，先要理解它比传统 RAG 好在哪里。


### 传统 RAG 的局限

传统 RAG（Baseline RAG）的工作流程是：将文档切成小块 → 生成向量 → 问题来了时用向量相似度检索最相关的几块 → 送给模型生成答案。

这个方案对"精确检索"类问题效果不错，但在两类场景下表现较差：

- 跨文档关联推理：当答案需要把分散在不同文档里的信息串联起来时，向量相似度无法表达这种"关系"。例如"A 公司的 CEO 和 B 公司的创始人有什么交集？"
- 全局性摘要问题：当问题要求对整个语料库做宏观总结时，几块文本片段根本无法覆盖全貌。例如"这批财报文件里最核心的风险点是什么？"


### GraphRAG 如何解决这两个问题

GraphRAG 的核心思路是：不直接检索文本块，而是先建立一张知识图谱，再基于图结构检索。

整个过程分为两个阶段：

GraphRAG 的索引阶段需要调用大量 LLM API，对每一段文本都做实体抽取和摘要，Token 消耗远高于传统 RAG。建议初次使用时先用小文档（几千字以内）测试流程，确认无误后再处理大规模语料。


### 四种查询模式对比


## 环境要求

在开始之前，请确认你的环境满足以下条件。


## 安装

GraphRAG 发布在 PyPI，建议在 Python 虚拟环境中安装，避免污染系统环境。


### 创建项目目录并初始化虚拟环境

```text
mkdir graphrag_demo
cd graphrag_demo
python -m venv .venv
```

```text
uv venv --python 3.12
```


### 激活虚拟环境

macOS / Linux：

```text
source .venv/bin/activate
```

Windows：

```text
.venv\Scripts\activate
```


### 安装 GraphRAG

```text
pip install graphrag
```

安装完成后验证：

```text
graphrag --help
```

会输出一些 graphrag 命令信息，输出类似：

GraphRAG 会自动安装 LiteLLM、LanceDB、pandas、numpy 等依赖。首次安装时间较长（通常 1~3 分钟），请耐心等待。


## 初始化工作区

运行 graphrag init 命令，GraphRAG 会在当前目录生成配置文件和目录结构。

```text
graphrag init
```

会提示我们设置模型，直接回车默认就好了，后面再修改：

```text
Specify the default chat model to use [gpt-4.1]:
Specify the default embedding model to use [text-embedding-3-large]:
```

初始化时会提示你输入默认的 Chat 模型和 Embedding 模型，可以暂时直接按 Enter 跳过，后面我们会手动修改 settings.yaml。

初始化完成后，目录结构如下：

```text
graphrag_demo/
├── .env                  # 存放 API Key 环境变量
├── settings.yaml         # 核心配置文件
├── input/                # 存放待处理的文本文件
├── output/               # 索引产物输出目录（自动生成）
└── prompts/              # Prompt 模板目录（自动生成）
```

每次升级 GraphRAG 小版本后，建议重新运行 graphrag init --force 刷新配置格式，否则可能因配置结构变更导致运行报错。注意该命令会覆盖现有的 settings.yaml 和 prompts，建议先备份。


## 准备测试文档

GraphRAG 支持 .txt、.csv、.json 格式的文档，所有待处理文件放在 input/ 目录下。

我们使用官方推荐的测试文档——查尔斯·狄更斯的《圣诞颂歌》，直接从 Project Gutenberg 下载：

```text
curl https://static.jyshare.com/download/pg24022.txt -o ./input/book.txt
```

如果网络不通，也可以自己创建一个中文测试文本，内容越丰富（含大量人物、地点、事件关系），GraphRAG 的知识图谱效果越明显：

文件放在 input 目录下，文件名为 demo.txt：

```text
SpaceX 太空探索技术公司成立于 2002 年，由埃隆·马斯克（Elon Musk）在美国加利福尼亚州霍桑市创办。
公司目标是大幅降低太空运输成本，最终实现人类移民火星。

马斯克早年联合创立了 PayPal，2002 年以 15 亿美元出售给 eBay，随后将个人资产投入 SpaceX。
联合创始人中，汤姆·穆勒（Tom Mueller）担任推进系统首席设计师，主导了 Merlin 和 Raptor 发动机的研发。
格温·肖特维尔（Gwynne Shotwell）于 2002 年加入，2008 年起担任总裁兼 COO，负责公司日常运营和商业拓展。

2008 年，猎鹰 1 号（Falcon 1）在经历三次失败后首次成功入轨，成为首个由私营公司研制的液体轨道火箭。
2010 年，猎鹰 9 号（Falcon 9）首飞成功，同年龙飞船（Dragon）完成首次商业发射与回收。
2012 年，龙飞船成为首个对接国际空间站的商业航天器。

2015 年 12 月，猎鹰 9 号一级火箭首次实现陆地垂直回收，开创了火箭重复使用的新纪元。
此后 SpaceX 累计完成超过 200 次火箭回收，单枚助推器最高复用次数达到 20 次以上。

2020 年，载人龙飞船（Crew Dragon）将 NASA 宇航员送入国际空间站，标志着商业载人航天时代的开始。
Starlink 星链项目自 2019 年启动，截至 2024 年已在轨部署超过 5000 颗卫星，覆盖全球超过 60 个国家和地区。

Starship 星舰是 SpaceX 正在研发的超重型运载系统，由超重助推器（Super Heavy）和星舰飞船组成，
设计目标为完全可重复使用，近地轨道运力超过 100 吨，是 NASA 阿尔忒弥斯登月计划的指定着陆器。

竞争对手方面，SpaceX 主要面临来自蓝色起源（Blue Origin）和联合发射联盟（ULA）的压力。
蓝色起源由亚马逊创始人杰夫·贝索斯创立，专注亚轨道旅游和重型火箭 New Glenn 的研发。
ULA 由洛克希德·马丁和波音合资成立，长期承担美国军方卫星发射任务。
```


## 配置 qwen-plus 与 Embedding 模型

这是整个教程最关键的步骤，需要修改 .env 和 settings.yaml 两个文件。


### 第一步：配置 API Key

打开 .env 文件，填入你的 API Key：


## 实例


### 第二步：修改 settings.yaml

打开 settings.yaml，将整个内容替换为以下配置。

GraphRAG 2.x 使用 LiteLLM 统一调用各家模型，model_provider: openai 配合 api_base 即可将请求转发到任意 OpenAI 兼容接口：

```text
completion_models:
  default_completion_model:
    model_provider: openai
    model: qwen-plus                              # 中文抽取稳定，成本低于 qwen-plus
    auth_method: api_key
    api_key: ${DASHSCOPE_API_KEY}
    api_base: https://dashscope.aliyuncs.com/compatible-mode/v1
    call_args:
      temperature: 0                              # 提高结构化稳定性
      max_tokens: 4096
    retry:
      type: exponential_backoff
      max_retries: 5
      base_delay: 2

embedding_models:
  default_embedding_model:
    model_provider: openai
    model: text-embedding-v4                      # 通义向量模型
    auth_method: api_key
    api_key: ${DASHSCOPE_API_KEY}
    api_base: https://dashscope.aliyuncs.com/compatible-mode/v1
    retry:
      type: exponential_backoff
      max_retries: 5

input:
  type: text

input_storage:
  type: file
  base_dir: input

chunking:
  type: tokens
  size: 600                                       # 中文推荐 500~800
  overlap: 100
  encoding_model: o200k_base

output_storage:
  type: file
  base_dir: output

reporting:
  type: file
  base_dir: logs

cache:
  type: json
  storage:
    type: file
    base_dir: cache

vector_store:
  type: lancedb
  db_uri: output/lancedb

embed_text:
  embedding_model_id: default_embedding_model    # 注意不要带逗号
  batch_size: 10                                 # 百炼 embedding 单次最多10条
  batch_max_tokens: 6000
  concurrency: 1                                 # 避免并发触发限流

extract_graph:
  completion_model_id: default_completion_model
  entity_types: []                               # 自动识别实体
  max_gleanings: 3                               # 提高关系补抽成功率

summarize_descriptions:
  completion_model_id: default_completion_model
  max_length: 500

cluster_graph:
  max_cluster_size: 20                           # 降低社区数量

extract_claims:
  enabled: false

community_reports:
  completion_model_id: default_completion_model
  max_length: 1500
  max_input_length: 4000                         # 防止生成阶段过慢

snapshots:
  graphml: true                                  # 导出图结构
  embeddings: false

local_search:
  completion_model_id: default_completion_model
  embedding_model_id: default_embedding_model
  top_k_entities: 10

global_search:
  completion_model_id: default_completion_model
  map_max_length: 500
  reduce_max_length: 1500
```

关于 Qwen 的 JSON 输出：GraphRAG 在实体抽取阶段需要模型稳定返回 JSON 格式。Qwen 支持 JSON 模式，将 temperature 设为 0 可以进一步提高输出稳定性，减少解析失败的概率。如果仍然出现 JSON 解析错误，可以尝试在 call_args 中添加 response_format: {type: json_object}。


## 开始索引

配置完成后，运行索引命令，GraphRAG 会自动读取 input/ 目录下的所有文件，调用 qwen-plus 进行实体抽取、关系识别、摘要生成，最终构建完整的知识图谱。

```text
graphrag index
```

你会看到类似如下的进度输出：

```text
⠹ GraphRAG Indexer
├── Loading Input (text) - 1 files loaded
├── create_base_text_units
├── extract_graph
│   └── Entity Extraction: 100%|████████████| 12/12 [02:34<00:00]
├── summarize_descriptions
├── cluster_graph
├── community_reports
└── generate_text_embeddings
All workflows completed successfully.
```

索引完成后，output/ 目录下会生成一系列 Parquet 文件：

索引时间参考：对于一篇几千字的中文文档（约 10~20 个文本块），使用 qwen-plus 大约需要 3~10 分钟；对于 10 万字以上的大型文档集，可能需要数小时。建议先用小文档跑通流程，再处理大规模数据。


## 执行查询

索引完成后，就可以对知识图谱进行查询了。GraphRAG 提供 CLI 和 Python API 两种方式。


### CLI 查询

全局搜索（适合宏观性问题）：

```text
graphrag query "文档中涉及的主要组织和人物有哪些？它们之间有什么关系？"
```

本地搜索（适合针对特定实体的问题），加 --method local：

```text
graphrag query "SpaceX 公司的主要业务和合作伙伴有哪些？" --method local
```

DRIFT 搜索（兼顾深度与广度）：

```text
graphrag query "埃隆·马斯克的职业背景和主要贡献是什么？" --method drift
```

基础向量搜索（与传统 RAG 对比）：

```text
graphrag query "Starship 星舰的设计目标和能力是什么？" --method basic
```


### Python API 查询

在代码中调用 GraphRAG 查询，适合集成到应用程序中。


## 实例

```text
python query_demo.py
```

```text
============================================================
【Global Search】全局性问题
============================================================
根据文档内容，主要涉及以下公司和人物关系网络：

**公司层面：**
- SpaceX 公司：主要角色，覆盖商业发射、载人航天、卫星互联网三大方向
- NASA：重要合作伙伴，阿尔忒弥斯登月计划 Starship 着陆器供应商
- 蓝色起源 / 联合发射联盟：主要竞争对手

**人物层面：**
- 马斯克（创始人）：PayPal 联合创始人，SpaceX CEO 兼首席工程师
- 汤姆·穆勒（联合创始人）：推进系统首席设计师，Merlin 和 Raptor 发动机之父
- 格温·肖特维尔：总裁兼 COO，负责公司商业运营

**关键关系：**
SpaceX 与 NASA 于 2020 年建立战略合作关系，
三家公司（SpaceX、蓝色起源、ULA）在商业航天发射市场形成竞争格局...

============================================================
【Local Search】针对特定实体的问题
============================================================
SpaceX 公司成立于 2002 年，创始团队包括：
- 马斯克：PayPal 联合创始人，SpaceX CEO 兼首席工程师，航天领域超二十年经验
- 汤姆·穆勒：推进系统首席设计师，主导 Merlin 和 Raptor 发动机研发

主要产品：
1. 猎鹰 9 号：全球首个实现垂直回收的轨道级火箭，已完成 200 次以上回收
2. Starship 星舰：超重型运载系统，近地轨道运力超 100 吨，完全可重复使用

检索到相关实体数量：12
```


## Prompt 自动调优

GraphRAG 官方强烈建议在处理自己的数据前，先运行 Prompt 自动调优。

自动调优会让 LLM 读取你的部分文档，然后生成针对你的数据领域定制化的实体抽取 Prompt，使知识图谱构建质量更高。

```text
graphrag prompt-tune --config settings.yaml --root . --language Chinese
```

调优完成后，prompts/ 目录下的 Prompt 文件会被自动更新。如果你的文档是中文的，加上 --language Chinese 参数可以让生成的 Prompt 也使用中文，提升中文实体抽取准确率。

Prompt 调优本身也会消耗 LLM Token（大约相当于对少量文档做一次快速索引），建议每次更换数据集时重新调优一次，而不是一直使用默认 Prompt。


## 常用 CLI 命令速查

以下是 GraphRAG 日常使用中最常用的命令。


## 完整 settings.yaml 字段说明

以下对 settings.yaml 中最常用的配置项做详细说明，方便进一步调整。


### 模型相关


## 后续章节

- 分块相关
- 实体抽取相关
- 常见问题
- 索引中途失败了怎么办？
- 出现 JSON 解析错误怎么处理？
- 如何选择 Global Search 还是 Local Search？
- Token 消耗太高如何控制？
- 如何处理中文文档？
- 延伸阅读

## 复习重点

- 能说明 `GraphRAG 入门教程` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
