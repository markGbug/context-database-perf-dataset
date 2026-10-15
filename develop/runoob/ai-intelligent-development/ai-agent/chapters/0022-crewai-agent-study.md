# AI Agent（智能体）：CrewAI 制作智能体

- 来源：[CrewAI 构建智能体](https://www.runoob.com/ai-agent/crewai-agent.html)
- 分类：AI / 智能开发
- 技术：AI Agent（智能体）
- 笔记类型：学习笔记
- 章节序号：0022

## 本章内容

CrewAI 是一个多智能体协作的开源框架，专门用于编排和协调多个 AI Agent 进行协作。

CrewAI 可以把一个复杂任务，拆成多个角色，各自负责一部分，通过流程协作完成。

对比理解：

- 单 Agent：一个大模型，从头干到尾
- CrewAI：产品经理 + 工程师 + 分析师 + 编辑，各司其职

CrewAI 是一个协调、管理和框架化 AI Agent 的工具，它基于 LangChain 和 Pydantic 构建，用于促进角色扮演、自治和协作的 Agent 团队。

- Crew（团队）： 一个由多个 Agent 组成的项目组。
- Agent（成员）： 团队中的个体，每个都有明确的 role（角色）、goal（目标）和 backstory（背景故事）。
- Task（任务）： 需要团队完成的具体工作。一个 Crew 包含多个有序或并行的 Task，并分配给合适的 Agent。
- Process（流程）： 定义团队的工作流程，例如是顺序执行还是同时执行任务。

简单来说，crewAI 提供了一个结构化的方式来定义谁（Agent）在什么流程（Process）下，完成哪些事（Task），最终达成团队目标。

下面的流程图清晰地展示了 crewAI 框架中各个核心组件是如何协同工作的：

流程始于定义具备特定角色和目标的智能体（Agent），然后为其创建具体的任务（Task）。

接着，将这些智能体及其任务组建成一个团队（Crew），并为团队选择协同工作的流程（Process），如顺序执行或并行执行。最终，团队按照既定流程执行所有任务，产出最终结果。


## 环境搭建与安装

开始构建前，我们需要准备好开发环境。


### 前置条件

Python 版本要求：

- 必须：Python ≥ 3.10 且 < 3.14
- 可以在终端输入 python --version 来检查，不满足版本范围，后续问题会非常多，不建议硬扛

CrewAI 使用 UV 做依赖和包管理，目的只有一个： 让多 Agent 项目更稳定，不被环境问题拖垮

UV 入门教程参考：UV - Python 包与环境管理工具。

API 密钥：

crewAI 本身不提供 AI 模型，它需要连接像 OpenAI 的 GPT、Anthropic 的 Claude 等大语言模型。


### 安装 crewAI

打开你的终端或命令行工具，使用 pip 命令安装 crewAI 包。

```text
# 正常安装
pip install crewai
# 其他依赖
pip install langchain
pip install openai


# 如果安装慢，可以使用国内镜像安装
pip install crewai -i https://mirrors.aliyun.com/pypi/simple/
pip install langchain -i https://mirrors.aliyun.com/pypi/simple/
pip install openai -i https://mirrors.aliyun.com/pypi/simple/
```

如果希望使用 crewAI 内置的一些高级工具（如网络搜索），可以安装额外的依赖项：

```text
# 正常安装
pip install 'crewai[tools]'

# 如果安装慢，可以使用国内镜像安装
pip install 'crewai[tools]' -i https://mirrors.aliyun.com/pypi/simple/
```

国内我们可以采用 DeepSeek 大模型来测试，如果还没有需要先去 https://platform.deepseek.com/api_keys 创建一个 API key。

DeepSeek 的 API 文档参考：https://api-docs.deepseek.com/zh-cn/。

安装完成后，创建一个新的 Python 文件，例如 my_first_crew.py，并导入必要的库。

CrewAI 的 LLM 对第三方模型（包括 DeepSeek）底层必须通过 LiteLLM，使用前我们需要先安装：

```text
pip install -U litellm
```


## 实例

接下来，就会开始执行任务，输出相关信息：

完成后就会把输出的内容写入到 python_data_cleaning_blog.md 文件中。

以下是代码中相关属性的说明。


### LLM（模型层）关键属性


### Agent（智能体）关键属性


### researcher（研究员）


### writer（写作）

结论 顺序流水线中，写作 Agent 应关闭 delegation，否则容易二次委托失败。


### Task（任务）关键属性

Task 通用字段:

research_task:

write_task:


### Crew（执行器）关键属性


### kickoff() 与输出结构


## crewai 命令

我们可以使用 crewai 命令生成完整工程结构：

```text
crewai create crew <项目名>
```

例如我们创建一个项目 runoob-agent-test，还行以下命令：

```text
crewai create crew runoob-agent-test
```

接下来出现以下内容，可以先选择大模型的提供商：

```text
Creating folder runoob_agent_test...
Cache expired or not found. Fetching provider data from the web...
Downloading  [####################################]  1102019/56339
Select a provider to set up:
1. openai
2. anthropic
3. gemini
4. nvidia_nim
5. groq
6. huggingface
7. ollama
8. watson
9. bedrock
10. azure
11. cerebras
12. sambanova
13. other
q. Quit
```

本章节，我们就选 DeepSeek，先输入 13 选 other，然后可以鼠标滚动看下 DeepSeek 在 23，输入序号 23 即可：

如果你有其他模型的 API key ，根据序号选择即可。

完成后，可以看到生成的目录如下：

项目结构说明:

```text
my_project/
├── .env                # 环境变量（API Key）
├── pyproject.toml      # 项目依赖声明
├── README.md
└── src/
    └── my_project/
        ├── main.py     # 程序入口
        ├── crew.py     # Crew 与 Agent 的核心逻辑
        ├── tools/      # 自定义工具
        └── config/
            ├── agents.yaml  # Agent 定义
            └── tasks.yaml   # Task 定义
```


### 运行你的 Crew

进入项目根目录：

```text
cd my_project
```

锁定并安装依赖：

```text
crewai install
```

运行：

```text
crewai run
```

或直接：

```text
python src/my_project/main.py
```


### 配置 API 密钥

为了安全起见，不建议将 API Key 直接写在代码里，我们可以将其设置为环境变量。

在代码中设置（仅用于测试）：

```text
import os
os.environ["OPENAI_API_KEY"] = "你的-openai-api-key-here"
```

推荐方式：使用 .env 文件

在项目根目录创建一个名为 .env 的文件。

在文件中写入：OPENAI_API_KEY=你的-openai-api-key-here

在 Python 代码中，使用 python-dotenv 包来加载。

安装命令：

```text
pip install python-dotenv
```

接下来在代码中载入：

```text
from dotenv import load_dotenv
load_dotenv() # 这会自动加载 .env 文件中的变量
# 现在 os.environ["OPENAI_API_KEY"] 就已经有了值
```


## 核心组件详解与实战

现在，让我们像组建公司一样，一步步创建我们的 AI 团队，我们将模拟一个技术博客创作团队。


### 第一步：定义智能体 (Agent)

Agent 是你的团队成员。创建时需要定义几个关键属性：

让我们创建两个代理：一个研究员和一个作家。


## 实例


### 第二步：创建任务 (Task)

Task 是具体的工作项，需要分配给 Agent 去完成。关键属性包括：

我们为研究员和作家各创建一个任务。


## 实例

注意 write_task 中的 context=[research_task]，这建立了任务间的依赖关系，意味着作家需要等研究员完成任务后才能开始工作。


### 第三步：组建团队与设置流程 (Crew & Process)

现在，将 Agent 和 Task 组装成 Crew，并定义他们的工作 Process。


## 实例

crewAI 主要支持两种流程：

- Process.sequential： 任务按在列表中的顺序依次执行。适合有严格依赖关系的流水线作业。
- Process.hierarchical： 配合一个管理者（Manager）Agent，由它来协调和分配任务。适合更复杂、动态的协作场景。


### 第四步：执行任务并获取结果

一切就绪，启动你的 AI 团队！


## 实例

运行你的 Python 脚本 (python my_first_crew.py)。由于我们设置了 verbose=True 和 verbose=2，你将在终端看到每个 Agent 的思考过程和任务执行日志，最后看到生成的博客文章。


## 进阶技巧：为 Agent 配备工具 (Tools)

crewAI 可以让 Agent 调用外部 Tool，如搜索网络、查询数据库、执行计算等。

以下示例为研究员配备网络搜索和计算工具：


## 后续章节

- 实例

## 复习重点

- 能说明 `CrewAI 构建智能体` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
