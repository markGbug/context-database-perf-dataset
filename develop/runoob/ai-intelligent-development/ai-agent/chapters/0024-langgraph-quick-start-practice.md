# AI Agent（智能体）：LangGraph 入门教程

- 来源：[LangGraph 入门教程](https://www.runoob.com/ai-agent/langgraph-quick-start.html)
- 分类：AI / 智能开发
- 技术：AI Agent（智能体）
- 笔记类型：练习笔记
- 章节序号：0024

## 本章内容

LangGraph 是由 LangChain 团队开发的一个低层级 Agent 编排框架，专为构建有状态（Stateful）、长时运行的 AI 工作流而设计。

与传统的线性 LLM 调用链不同，LangGraph 将工作流建模为有向图（Directed Graph）：

- 节点（Node）：执行具体操作的函数（如调用 LLM、执行工具、处理数据）
- 边（Edge）：定义节点之间的流转路径，支持条件分支
- 状态（State）：在整个工作流中共享并传递的数据

开源地址：https://github.com/langchain-ai/langgraph。

想象你正在指挥一场交响乐演出：传统的 LLM Chain 就像演奏一首从头到尾的曲子，只能顺序播放；而 LangGraph 则像一位指挥家，可以根据现场观众的反应随时调整演奏顺序，让某个乐章重复，或者跳转到特定段落。它让 AI 工作流拥有了"指挥"的智慧——能够循环、分支、回溯，真正实现复杂的自主决策。


### 为什么选择 LangGraph？

下表对比了传统 LLM Chain 与 LangGraph 的主要差异：


### 适用场景

- 对话机器人：需要记忆多轮对话上下文
- 自主 Agent：能够规划、使用工具、迭代思考
- 多 Agent 系统：多个 AI 协同完成复杂任务
- 审批工作流：需要人工审核的自动化流程
- 研究助手：需要多步骤推理和信息检索


## 核心概念

在开始编写代码之前，先理解 LangGraph 的三大核心概念。


### Graph（图）

Graph 是整个工作流的蓝图，定义了 Agent 的完整逻辑结构。它由节点（Nodes）和边（Edges）组成：

```text
StateGraph
   |-- Nodes（节点）
   |     |-- node_a
   |     |-- node_b
   |     +-- node_c
   +-- Edges（边）
         |-- START -> node_a
         |-- node_a -> node_b（条件边）
         |-- node_a -> node_c（条件边）
         +-- node_b -> END
```


### State（状态）

State 是贯穿整个图的共享数据结构。每个节点可以读取和更新 State，更新后的 State 会传递给下一个节点。

```java
from typing import TypedDict, Annotated
from langgraph.graph import add_messages

class MyState(TypedDict):
    messages: Annotated[list, add_messages]  # 消息列表（自动追加）
    user_name: str                            # 用户名称
    step_count: int                           # 步骤计数
```


### Nodes（节点）

节点是普通的 Python 函数，接收当前 State，返回更新后的 State（部分字段）。

```text
def my_node(state: MyState) -> dict:
    # 读取状态
    messages = state["messages"]

    # 执行操作...
    result = "处理结果"

    # 返回更新的字段（不需要返回所有字段）
    return {"messages": [{"role": "ai", "content": result}]}
```


### Edges（边）

边定义节点之间的流转方式：

- 普通边：固定路径，node_a -> node_b
- 条件边：根据 State 动态路由，node_a -> node_b 或 node_c
- 起始边：START -> 第一个节点
- 结束边：某节点 -> END


## 环境搭建


### 安装依赖

使用国内镜像安装 LangGraph 和相关依赖：

```text
# 创建虚拟环境（推荐）
python -m venv venv
source venv/bin/activate      # macOS/Linux
# venv\Scripts\activate       # Windows

# 安装 LangGraph 和 LangChain
pip install langgraph langchain langchain-openai python-dotenv -i https://mirrors.aliyun.com/pypi/simple/

# 可选：安装开发工具
pip install langgraph-cli jupyter -i https://mirrors.aliyun.com/pypi/simple/
```


### 配置 API Key

在项目根目录创建 .env 文件，同时配置 OpenAI 和 DeepSeek：

```text
# .env 文件内容

# OpenAI 配置（国外用户）
OPENAI_API_KEY=sk-xxx
OPENAI_BASE_URL=https://api.openai.com/v1

# DeepSeek 配置（国内用户推荐）
DEEPSEEK_API_KEY=sk-xxx
DEEPSEEK_BASE_URL=https://api.deepseek.com
DEEPSEEK_MODEL=deepseek-v4-pro
```


### 验证安装

```text
import langgraph
print(f"LangGraph 版本: {langgraph.__version__}")
```


## 第一个 LangGraph 程序

让我们从最简单的例子开始——一个只有两个节点的线性工作流。


## 实例

运行结果：

```text
[greet_node] 收到消息: 世界
[process_node] 处理消息: 你好！世界

最终结果: {'message': '你好！世界', 'processed': True}
```


### 可视化图结构

在 Jupyter Notebook 中可以直接可视化图结构：

```text
# 在 Jupyter Notebook 中可视化
from IPython.display import Image
Image(graph.get_graph().draw_mermaid_png())

# 或者打印 Mermaid 格式
print(graph.get_graph().draw_mermaid())
```


## State 状态管理


### 使用 TypedDict 定义状态

```text
from typing import TypedDict, Annotated, Optional
from langgraph.graph.message import add_messages

class AgentState(TypedDict):
    # 消息历史（add_messages reducer 自动追加而非覆盖）
    messages: Annotated[list, add_messages]

    # 普通字段（直接覆盖）
    user_id: str
    session_id: str

    # 可选字段
    error: Optional[str]

    # 计数器（使用 operator.add 作为 reducer）
    retry_count: Annotated[int, lambda x, y: x + y]
```


### 使用 Pydantic 定义状态（推荐用于生产）

```text
from pydantic import BaseModel, Field
from typing import Annotated
from langgraph.graph.message import add_messages

class ProductionState(BaseModel):
    messages: Annotated[list, add_messages] = Field(default_factory=list)
    user_id: str = ""
    confidence_score: float = 0.0

    class Config:
        arbitrary_types_allowed = True
```


### MessagesState（内置快捷状态）

LangGraph 提供了内置的 MessagesState，专为对话场景设计：

```text
from langgraph.graph import MessagesState

# MessagesState 等价于:
# class MessagesState(TypedDict):
#     messages: Annotated[list[AnyMessage], add_messages]

# 直接使用，无需自定义
builder = StateGraph(MessagesState)
```


## Nodes 节点


### 普通函数节点

```text
def simple_node(state: AgentState) -> dict:
    # 读取状态
    last_message = state["messages"][-1]

    # 执行操作
    response = f"收到: {last_message.content}"

    # 返回部分状态更新
    return {
        "messages": [{"role": "assistant", "content": response}]
    }
```


### LLM 调用节点


## 实例


### 异步节点

```text
import asyncio

async def async_node(state: AgentState) -> dict:
    """异步节点，适合 I/O 密集型操作"""
    # 模拟异步操作（如 API 调用、数据库查询）
    await asyncio.sleep(0.1)

    result = await some_async_api_call(state["messages"][-1].content)
    return {"messages": [{"role": "assistant", "content": result}]}

# 使用异步图
result = await graph.ainvoke({"messages": [...]})
```


### 使用类作为节点

```text
class RouterNode:
    def __init__(self, llm, system_prompt: str):
        self.llm = llm
        self.system_prompt = system_prompt

    def __call__(self, state: AgentState) -> dict:
        """类实例可以作为节点使用"""
        messages = [
            SystemMessage(content=self.system_prompt),
            *state["messages"]
        ]
        response = self.llm.invoke(messages)
        return {"messages": [response]}

# 添加类节点
router = RouterNode(llm, "你是一个专业的路由助手。")
builder.add_node("router", router)
```


## 后续章节

- Edges 边与条件路由
- 普通边
- 条件边
- 并行执行（Fan-out）
- 完整条件路由示例
- 实例
- 构建对话机器人
- 实例
- 工具调用 - ReAct Agent
- 定义工具
- 构建 ReAct Agent
- 实例
- 流式输出工具调用过程
- Human-in-the-Loop 人机协作
- 使用 interrupt 暂停执行
- 完整的审批工作流

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `LangGraph 入门教程` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
