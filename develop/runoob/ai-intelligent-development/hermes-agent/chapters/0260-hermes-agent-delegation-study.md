# Hermes Agent：Hermes Agent 子 Agent 委托与批量处理

- 来源：[Hermes Agent 委托](https://www.runoob.com/hermes-agent/hermes-agent-delegation.html)
- 分类：AI / 智能开发
- 技术：Hermes Agent
- 笔记类型：学习笔记
- 章节序号：0260

## 本章内容

本章介绍 Hermes 的两种并行处理能力：子 Agent 委托让一个主 Agent 将任务分发给多个子 Agent 并行执行，批量处理系统则能在数百个 Prompt 上并行运行 Agent 并生成结构化训练数据。


## 子 Agent 委托与并行

Hermes 支持从主 Agent 中委托任务给子 Agent，实现并行工作流。

子 Agent 通过 delegation 工具集实现：


## 实例

主 Agent 使用 spawn_agent 或 spawn_parallel 工具派生子 Agent。

以下伪代码说明并行委托的机制：


## 实例


### 后台任务

在会话中直接启动后台任务：


## 实例


### Kanban 多 Agent 协作

Kanban 工具集提供更结构化的多 Agent 协作——一个编排者 Agent 将任务分发到看板，多个工作者 Agent 认领并执行：


## 实例

Kanban 工具集需要显式启用——即使是 all 或 * 也不会自动开启它。这是有意设计，因为多 Agent 协作会消耗更多 Token。


## 批量处理与 RL 训练数据生成

批量处理让你在数百或数千个 Prompt 上并行运行 Agent，生成结构化的轨迹数据——主要用于模型微调训练数据生成和评估。


### 快速上手


## 实例


### 数据集格式

每行一个 JSON 对象，必须包含 prompt 字段，可选包含额外上下文：


## 实例


### 主要参数


### 输出结构

批量处理生成如下目录结构：

```text
data/my_first_run/
├── trajectories.jsonl    # 最终合并输出（所有批次）
├── batch_0.jsonl         # 各批次结果
├── batch_1.jsonl
├── checkpoint.json       # 断点续传记录
└── statistics.json       # 工具使用统计
```

每条轨迹以 ShareGPT 格式输出，包含完整对话历史、工具调用记录和推理覆盖率统计：


## 实例


### 质量过滤

批量运行结束后自动应用两项过滤：

推理痕迹指 <REASONING_SCRATCHPAD> 标记或原生 thinking tokens。过滤后的数据更适合用于模型微调。


### 与 Atropos RL 环境集成

批量处理可直接生成 Atropos 兼容的训练数据：


## 实例


## 复习重点

- 能说明 `Hermes Agent 委托` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
