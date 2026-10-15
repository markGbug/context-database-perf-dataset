# AI Agent（智能体）：Dify 入门教程

- 来源：[Dify 入门教程](https://www.runoob.com/ai-agent/dify-usage.html)
- 分类：AI / 智能开发
- 技术：AI Agent（智能体）
- 笔记类型：练习笔记
- 章节序号：0031

## 本章内容

Dify（Do It For You）是当前最受欢迎的开源 LLM 应用开发平台，专为构建由大型语言模型（LLM）驱动的生成式 AI 应用而设计。

Dify 将 AI 工作流编排、RAG 知识库、Agent 框架、模型管理、可观测性整合在一个可视化平台里，让你快速从原型走向生产，无需从零搭建 LLM 基础设施。

Dify 通过集成 RAG 流水线、AI 工作流、可观测性工具和模型管理，简化了 AI 应用的创建过程。

如果说 LangChain 是AI 应用的零件工厂（灵活但需要大量手写代码），那 Dify 就是 AI 应用的可视化 IDE ——组件都在，拖拽连线就能跑。


### 和其他工具的对比

以下是 Dify 与 LangChain、n8n 在关键维度上的对比。

Dify 的直观可视化编排工作室使其成为需要快速构建功能性 AI 应用的初创公司和企业的理想选择。

LangChain 则更适合需要自定义集成和开发者深度参与的企业级复杂应用。


### 谁在用 Dify？

从生物医学到汽车行业，Dify 为各类企业提供可靠的解决方案。

Volvo Cars 在 AI 前沿战略导航中使用 Dify 快速验证想法。

用户对 Dify 的高度评价是其能够将 AI Agent 开发民主化，将强大的 AI/ML 能力结合到无代码平台上。


## 核心概念

在开始操作之前，我们先了解一下 Dify 的基本概念：


## 安装与启动

四种安装方式，从零秒上手到高可用集群部署。


### 方式一：Dify Cloud（最快，0 秒上手）

访问 cloud.dify.ai，注册账号即可立即使用。

免费的 Sandbox 套餐包含每月 200 条消息和 5 个应用，无需配置任何环境。

适合快速体验、个人项目、测试原型。


### 方式二：Docker Compose 自托管（推荐生产使用）

适合有技术背景的用户，完全掌控数据和部署环境。

第一步：克隆仓库

克隆 Dify 仓库到本地:

```text
git clone https://github.com/langgenius/dify.git
cd dify
```

第二步：进入 docker 目录，复制环境配置

```text
cd docker
# 从模板复制环境配置文件
cp .env.example .env
```

第三步（重要）：配置 SECRET_KEY

从 v1.14.1 起，Docker 部署不再依赖公开的默认密钥。当 SECRET_KEY 为空时，API 会自动生成并持久化一个运行时密钥。建议在 .env 文件中明确设置。

```text
# 生成一个安全的随机密钥
openssl rand -base64 42
```

编辑 .env 文件，找到 SECRET_KEY 并设置为上面生成的随机字符串：

```text
SECRET_KEY=your-very-long-random-secret-key-here
```

第四步：启动服务

```text
# 启动所有 Dify 服务（首次会拉取镜像，约需 3-10 分钟）
docker compose up -d
```

第五步：访问并初始化

浏览器访问 http://localhost/install，完成管理员账号注册。

第六步：验证服务状态

```text
# 查看所有容器状态，全部为 healthy 即表示运行正常
docker compose ps
```

所有容器（api、worker、web、db、redis、weaviate、nginx 等）状态均为 healthy 即表示运行正常。

```text
# 停止所有服务（数据保留在 Docker volumes 中）
docker compose down

# 重新启动所有服务
docker compose up -d
```

```text
# 进入 docker 目录
cd dify/docker

# 拉取最新代码
git pull origin main

# 拉取新镜像
docker compose pull

# 重新启动
docker compose up -d
```

数据持久化在 Docker volumes 中，更新不会影响已有的应用、知识库或对话历史。在大版本升级前建议备份 PostgreSQL 数据库。


### 方式三：AWS Marketplace 一键部署

面向在 AWS 上运营的初创公司和小型企业，可以通过 AWS Marketplace 上的 Dify Premium 实现一键部署到自己的 AWS VPC，还支持自定义 Logo 和品牌。


### 方式四：Kubernetes 部署（高可用）

对于需要高可用配置的场景，社区提供了 Helm Charts 和 YAML 文件，可以将 Dify 部署到 Kubernetes 集群。

```text
# 添加 Dify Helm 仓库
helm repo add dify https://langgenius.github.io/dify-helm

# 使用自定义 values.yaml 安装
helm install dify dify/dify -f values.yaml
```


## 配置模型提供商

安装完成后，第一步是连接你的 AI 模型。


### 操作路径

登录 Dify 后，点击右上角头像，进入 Settings（设置），选择 Model Provider（模型提供商）。

比如我们可以安装 DeepSeek 这个模型供应商，然后配置 API key：


### 主流提供商配置

Anthropic（Claude 系列）：

```text
Provider: Anthropic
API Key: sk-ant-xxxxxxxx（从 console.anthropic.com 获取）
推荐模型：claude-sonnet-4-6（综合性能最佳）
```

OpenAI：

```text
Provider: OpenAI
API Key: sk-xxxxxxxx（从 platform.openai.com 获取）
推荐模型：gpt-4o（性价比高）
```

Google（Gemini 系列）：

```text
Provider: Google
API Key: xxxxxxxx（从 aistudio.google.com 获取）
推荐模型：gemini-2.0-flash（速度快，适合大量请求）
```

OpenRouter（一个 Key 访问 300+ 模型）：

```text
Provider: OpenRouter
API Key: sk-or-xxxxxxxx（从 openrouter.ai 获取）
Base URL: https://openrouter.ai/api/v1
```

本地模型（Ollama）：

```text
Provider: Ollama
Base URL: http://host.docker.internal:11434  # Docker 内访问宿主机
（先在宿主机运行：ollama pull llama3.3）
```


### 配置 Embedding 模型（知识库必需）

知识库的向量化需要 Embedding 模型，以下是推荐选项：


### 验证模型可用

回到 Settings，找到已配置的提供商，点击模型名旁边的 Test 按钮，显示绿色勾号则配置成功。


## 五种应用类型详解

在 Dify 首页点击 Create App（创建应用），会看到五种类型，每种对应不同的使用场景。

点击创建空白应用，可以看到五种类型的应用：


### 1. Chatbot（聊天助手）

标准的多轮对话应用，有持久的会话记忆。


### 2. Text Generator（文本生成器）

单次输入到单次输出，不保留对话历史。


### 3. Agent（智能体）

能主动调用工具、自主规划和执行多步骤任务的 AI。


### 4. Chatflow（对话流）

在 Workflow 的基础上加入多轮对话能力，兼具流程编排和会话上下文。


### 5. Workflow（工作流）

纯自动化的多步骤处理流程，不带对话界面，通过 API 触发或手动运行。


### 选择指南

根据需求快速决定使用哪种应用类型：

```text
需要多轮对话？
├─ 是 → 需要复杂流程逻辑？
│        ├─ 是 → Chatflow
│        └─ 否 → Chatbot 或 Agent（需要工具调用时选 Agent）
└─ 否 → 单次输入输出？
          ├─ 是 → Text Generator
          └─ 需要多步骤自动化 → Workflow
```


## 知识库（RAG）：让 AI 回答你的私有数据

知识库是 Dify 最强大的功能之一，也是大多数企业应用的核心。


### 创建知识库

- 导航栏选择 Knowledge（知识库），点击 Create Knowledge（创建知识库）
- 给知识库命名，如「产品手册」或「内部政策文件」
- 选择创建方式

Dify 接受 PDF、Word（.docx）、Markdown（.md）、纯文本（.txt）、CSV 和 HTML 格式的文件。

推荐使用 Markdown 或纯文本，它们解析最可靠。

布局复杂或扫描版的 PDF 可能需要预处理，建议先用 OCR 工具提取文本后再上传。

Knowledge Pipeline 是一个可视化的节点式编排系统，专门用于文档摄取处理。

它解决了传统 RAG 的三大痛点：分散的数据源、解析过程中的信息丢失（图表和公式被丢弃）、以及黑盒处理过程（难以诊断失败原因）。

通过 API 同步现有的外部知识库，无需数据迁移。


### 文档分块策略

上传后，Dify 会自动进行文本分块（Chunking）。关键参数说明如下：

中文内容建议分块大小设置在 500 Token 左右。太长会让检索不够精准，太短会丢失上下文。


### 索引模式


## 后续章节

- 检索配置
- 测试检索效果
- 将知识库关联到应用
- Workflow 工作流：可视化编排多步骤任务
- 进入 Workflow 编辑器
- 主要节点类型
- 节点间的变量传递
- Human Input 节点（HITL）
- 调试工作流
- 场景实战一：企业内部知识问答机器人
- 业务背景
- 步骤一：准备知识库
- 步骤二：创建 Chatbot 应用
- 步骤三：测试与调优
- 步骤四：发布与集成
- 场景实战二：自动化内容生成流水线

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Dify 入门教程` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
