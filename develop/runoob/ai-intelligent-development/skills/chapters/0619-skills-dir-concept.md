# Skills（技能）：Skills 目录结构

- 来源：[Skills 目录结构](https://www.runoob.com/skills/skills-dir.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：概念卡
- 章节序号：0619

## 本章内容

理解 Skill 的目录结构和运行机制，是构建可维护、可复用 AI Agent 能力的基础。

本文从零开始拆解一个标准 Skill 的目录结构、各文件作用和完整工作流程。


## 什么是 Skill

Skill 是一个独立的能力单元，用来完成某一类特定任务。

如果把 Agent 比作操作系统，Skill 就像应用程序；如果把 Agent 比作项目经理，Skill 就是可以被调用的专业能力。


### Skill 的常见类型

以下是一些典型的 Skill 应用场景：


### Skill 与 Agent 的关系

Skill 本身不负责决定什么时候使用，真正负责决策的是 Agent。

完整的工作流程如下：

关键要点：Agent 不会一次性加载所有 Skill 的完整内容。它会先读取每个 Skill 的描述信息，命中目标 Skill 后再加载完整内容。这样做的原因是：如果有几百个 Skills，每次都全部加载会极其浪费 Token。


## Skill 的标准目录结构

一个完整的 Skill 不是单个文件，而是包含多个文件的目录。

以下是一个标准 Skill 的完整目录结构：

```text
my-skill/
│
├── SKILL.md          ← 核心执行文件
├── metadata.json     ← 元信息
├── examples/         ← 示例目录
│   ├── example1.md
│   └── example2.md
│
├── scripts/          ← 可执行脚本
│   ├── main.py
│   └── utils.py
│
├── resources/        ← 资源目录
│   ├── prompt.md
│   └── config.yaml
│
├── tests/            ← 测试目录
│   ├── test_cases.md
│   └── eval.yaml
│
├── README.md         ← 使用说明
│
└── CHANGELOG.md      ← 变更日志
```

接下来逐个拆解每个文件和目录的作用。


## SKILL.md：核心执行文件

这是 Skill 中最重要的文件，定义了 Skill 的所有执行逻辑。

它包含以下关键信息：

以下是一个规范的 SKILL.md 示例：


## 实例


### 常见的错误写法

很多初学者会写出过于简略的 SKILL.md，例如：


## 不推荐写法

这种写法的问题在于：不知道什么时候使用、不知道什么时候不用、输出格式不明确、容易和其他 Skill 冲突。

一个合格的 SKILL.md 应该让 Agent 一眼就能判断：这个 Skill 适不适合当前任务。


## metadata.json：Skill 元信息

这个文件提供机器可读的结构化数据，帮助 Agent 快速筛选 Skill。


## 实例


### 常见字段说明

其中 description 字段最为重要，因为 Agent 通常依靠它做匹配。

匹配过程大致如下：用户提出请求后，Agent 扫描所有 Skill 的 description，发现匹配的描述后加载完整的 Skill 内容并执行。


## examples：示例目录

很多开发者忽略这一部分，但它实际上非常重要。


### 目录结构

```text
examples/
├── example1.md
├── example2.md
```


### 示例文件内容


## 实例


### examples 的作用

经验上，好的 examples 往往比增加提示词更有效。


## scripts：可执行脚本

Skill 不仅仅是提示词，有时需要真正执行代码来完成实际工作。

常见需要脚本的场景包括：读取 PDF、执行 OCR、调用数据库、数据处理、生成图表等。


### 目录结构

```text
scripts/
├── main.py
└── utils.py
```


### Python 脚本示例


## 实例

Skill 的工作流程是：读取文件 → 执行脚本 → 获取结果，然后再将结果交给大模型处理。


## resources：资源目录

用于保存辅助内容，将配置与代码分离。


### 目录结构

```text
resources/
├── prompt.md
├── config.yaml
```


### 可能包含的资源类型


### 配置文件示例


## 后续章节

- 实例
- tests：测试目录
- 目录结构
- 测试用例示例
- 实例
- 测试的作用
- README：使用说明
- 实例
- 完整案例：PDF 分析 Skill
- 目录结构总览
- 完整调用流程
- 为什么 Skill 要设计成目录结构
- 单文件方案的问题
- 目录化方案的优势
- 总结
- 核心文件关系

## 记忆卡片

- 一句话定义：`Skills 目录结构` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
