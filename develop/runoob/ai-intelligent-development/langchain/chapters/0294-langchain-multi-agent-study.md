# LangChain：LangChain 多 Agent——多智能体协作

- 来源：[LangChain 多 Agent](https://www.runoob.com/langchain/langchain-multi-agent.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：学习笔记
- 章节序号：0294

## 本章内容

当任务涉及多个不同领域，或者单个 Agent 需要处理大量工具和复杂流程时，可以考虑使用 Multi-agent（多智能体） 架构。

多 Agent 的核心思想，是将复杂任务拆分成多个相对独立的子任务，让不同 Agent 负责不同领域，再由协调者汇总结果。

例如，一个编程学习助手可以分成课程检索 Agent、代码分析 Agent 和学习规划 Agent。每个 Agent 使用自己的 System Prompt 和工具，不需要掌握所有业务细节。

本章节基于 LangChain 1.x，介绍 Subagents、Supervisor、Router、Handoffs、顺序工作流及多 Agent 的上下文管理。


## 一、为什么需要多 Agent？

单个 Agent 可以完成很多工作，但当任务复杂度持续增加时，可能遇到以下问题：

- 上下文过多：大量系统提示词、文档和工具结果占用上下文窗口。
- 工具选择困难：可用工具较多时，模型可能选择错误的工具或参数。
- 专业能力混杂：不同任务需要不同的处理规则和数据来源。
- 维护复杂：所有业务逻辑集中在一个 Agent 中，修改和测试比较困难。

多 Agent 可以把任务拆分为独立模块，每个 Agent 只接收完成当前任务需要的信息。

但需要注意，多 Agent 并不一定提高回答准确率，也不一定降低成本。

因为每个子 Agent 都可能产生额外的模型调用、Token 消耗和网络延迟。


### 单 Agent 与多 Agent 对比

建议：如果使用一个 Agent 加上合理的工具分组就能解决问题，没有必要为了使用多 Agent 而增加架构复杂度。


## 二、LangChain 多 Agent 架构模式

LangChain 官方主要介绍以下几种协作模式：

其中，最容易入门的方式是 Subagents（子 Agent 作为工具）。


## 三、方式一：子 Agent 作为工具

Subagents 模式也称为 Supervisor 模式。

它包含一个主 Agent（协调者），以及多个具备专业能力的子 Agent。

执行流程：

```text
                 用户问题
                    |
                    v
              主 Agent
              Supervisor
                    |
          +---------+---------+
          |                   |
          v                   v
      课程 Agent          计算 Agent
          |                   |
      查询课程目录          数学计算
          |                   |
          +---------+---------+
                    |
                    v
              主 Agent 汇总
                    |
                    v
                 最终回答
```

主 Agent 不需要掌握每个子 Agent 的全部内部工具，只需要知道什么时候调用对应的专家。


### 基本实现方式

先创建子 Agent：

```text
subagent = create_agent(
    model="deepseek:deepseek-flash",
    tools=[...],
    system_prompt="你是专业助手。"
)
```

然后将它包装成工具：

```text
@tool
def ask_expert(question: str) -> str:
    """向专业 Agent 咨询。"""
    result = subagent.invoke({
        "messages": [{"role": "user", "content": question}]
    })
    return result["messages"][-1].content
```

最后让主 Agent 调用该工具：

```text
coordinator = create_agent(
    model="deepseek:deepseek-flash",
    tools=[ask_expert]
)
```

这里的子 Agent 虽然是独立的 CompiledStateGraph，但父 Agent 是通过 Python 工具函数调用它，而不是自动将子图节点合并到父图中。


## 四、完整实例：课程专家与数学专家协作

下面创建三个 Agent：

- 课程专家：查询模拟编程课程。
- 数学专家：进行数值计算。
- 主 Agent：分析用户问题，调用专家并整理答案。

本示例不使用 eval() 执行模型生成的表达式，而是定义具有明确参数的数学工具。

文件名：multi_agent_demo.py

安装依赖：

```text
pip install -U langchain langgraph langchain-deepseek python-dotenv
```

配置 .env：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
```


## 完整实例


### 可能的运行结果

```text
[协调者] 调用课程专家
[协调者] 调用数学专家

最终回答：
可以学习 Python3 基础教程，适合编程初学者。

另外，25 摄氏度等于 77 华氏度。
```

这是多 Agent 最典型的用法：主 Agent 不负责具体计算和课程查询，而是将任务委派给对应的专业 Agent。

注意：模型不保证按照固定顺序调用专家，也可能只调用其中一个。因此以上日志和回复仅作为可能的运行结果。


## 五、子 Agent 的上下文隔离

Subagents 模式的重要价值之一，是减少不相关的上下文进入子任务。

例如，用户在主 Agent 中连续讨论了多个主题：

```text
1. Python 课程
2. Java 基础
3. 数据库优化
4. 温度计算
```

当主 Agent 调用数学专家时，可以只发送当前数学问题：

```text
25 摄氏度等于多少华氏度？
```

数学专家不需要处理前面所有课程和数据库相关的聊天记录。

这样可以降低子任务的上下文干扰。


### 默认无状态

如果子 Agent 没有配置 Checkpointer，并且每次都使用独立的消息输入，那么不同调用之间不会自动保留子 Agent 的历史对话。

例如：

```text
result = math_agent.invoke({
    "messages": [{"role": "user", "content": question}]
})
```

每次只发送当前问题，形成独立的子任务上下文。

如果子 Agent 需要多轮记忆，可以额外配置 Checkpointer，但必须仔细设计 thread_id、用户隔离和任务作用域。

注意：主 Agent 不会自动获得子 Agent 的全部执行消息。上面的工具只把子 Agent 最终回答返回给了主 Agent。


## 六、name 参数：为 Agent 命名

可以通过 create_agent(name=...) 为 Agent 指定名称。


### 实例


## 实例

name 主要用于标识 Agent 图，有助于调试、追踪和嵌入更复杂的图结构。

建议使用有意义的名称：

```text
course_expert
math_expert
code_reviewer
learning_planner
coordinator
```

但需要注意，不能假设设置 name 后，所有 AIMessage 都会自动带上该名称。

在前面的工具包装模式中，如果需要区分执行来源，可以通过工具名称、日志和追踪信息进行标记。


## 七、方式二：Router 任务路由

如果业务只需要判断用户的问题属于哪个领域，再交给对应 Agent 处理，那么未必需要一个拥有多个工具的主 Agent。

可以直接创建 Router（路由器）。

流程：

```text
用户问题
    |
    v
任务分类 Router
    |
    +---- 课程问题 ---- 课程 Agent
    |
    +---- 数学问题 ---- 数学 Agent
    |
    +---- 其他问题 ---- 通用 Agent
```

Router 主要负责判断任务类型，专业 Agent 负责实际处理。

对于任务类型明确的系统，这种结构通常更容易维护和测试。


### 实例：根据任务类型选择 Agent


## 实例

这里使用 Pydantic 将路由结果限制为三个值：

```text
course
math
general
```

不同于协调者模式，Router 在这个例子中只选择一个 Agent。

如果需要将问题拆分成多个领域并行处理，应使用更完整的 Router 工作流或 Supervisor 模式。

注意：Router 的分类结果也可能出错，需要根据实际业务测试分类准确率。对于简单、固定的规则，也可以直接使用 Python 条件判断，不必额外调用模型。


## 八、方式三：顺序工作流

有些任务具有明确的执行顺序，例如：

```text
生成文章
    ↓
检查技术事实
    ↓
润色文章
    ↓
输出最终内容
```

这种流程不一定需要由主 Agent 动态选择下一步。

如果执行顺序固定，可以直接通过 Python 或 LangGraph 构建确定性工作流。


### 实例：文章生成与审核


## 实例

这个例子创建了两个 Agent，但并没有创建协调者。

因为任务顺序已经确定：

```text
Writer → Reviewer
```

这种方式通常比让协调者反复决定下一步更直接。

注意：第二个 Agent 只能根据自身能力识别潜在问题，并不能自动保证技术事实正确。如果需要事实核查，应提供可信文档、测试工具或其他数据来源。


## 九、方式四：Handoffs 控制权交接

Handoffs 与 Supervisor 不同。

Supervisor 由主 Agent 统一调用子 Agent，而 Handoffs 允许执行流程根据当前状态切换到另一个专业处理阶段。

例如，在线客服：

```text
普通客服
    ↓
判断用户需要退款
    ↓
切换到退款处理阶段
    ↓
退款助手处理相关流程
    ↓
必要时进入人工审批
    ↓
完成处理
```

这种模式适合具有明确阶段切换的业务，例如：

- 普通客服转订单客服。
- 技术支持转售后处理。
- 问题收集转人工审核。
- 资料审核完成后进入执行阶段。

Handoffs 通常需要维护当前活动阶段，例如：

```text
active_agent = "support"

active_agent = "refund"
```

在 LangChain 中，可以通过工具调用更新状态，再根据状态调整当前使用的 Prompt 和工具。

如果需要多个独立图节点相互交接控制权，也可以使用 LangGraph 构建更明确的 Handoff 工作流。

注意：Handoff 不代表自动获得更高权限。进入退款、支付或删除等阶段后，仍然必须执行后端权限校验和必要的人工审批。


## 十、Middleware 与多 Agent 路由

Middleware 可以动态修改模型请求的工具列表或系统提示词，但它本身并不等于多 Agent 系统。

例如，根据用户角色调整当前 Agent 可使用的工具：

```text
普通用户 → 查询工具
管理员 → 查询工具 + 管理工具
```

这属于 动态工具选择，不一定需要创建两个独立 Agent。


### 实例：使用 wrap_model_call 过滤工具


## 实例

这里普通用户不会在当前模型请求中看到 delete_course 的工具定义。

但需要特别强调，动态隐藏工具不等于真正的权限隔离。

如果工具具有真实删除、支付或管理能力，工具执行层仍必须验证可信用户身份和权限。

如果需要完全确定性的安全隔离，更稳妥的方式是根据后端权限创建不同工具集合，或在受信任的工具执行入口再次强制校验。


## 十一、多 Agent 的消息与记忆管理

多 Agent 系统不仅需要管理任务，还需要明确各 Agent 能够访问哪些上下文。

常见有三种方式：

例如，课程专家可以获得：

```text
用户当前学习等级：入门
用户想学习：Python
任务：推荐适合的课程
```

而不需要获得用户全部历史消息。

这就是多 Agent 中非常重要的 Context Engineering（上下文工程）。

通过合理分配上下文，可以减少无关数据，提高各专业 Agent 的任务聚焦程度。

注意：不要把其他用户的完整对话历史、密钥或不相关的敏感信息传入子 Agent。


## 后续章节

- 十二、并行执行多个子 Agent
- 实例：并发获取两个专家的回答
- 实例
- 十三、如何选择多 Agent 架构？
- 十四、生产环境的注意事项
- 1、控制模型调用成本
- 2、限制任务委派层级
- 3、不要使用 eval() 执行模型生成的代码
- 4、子 Agent 应保持最小权限
- 5、明确输入输出协议
- 6、合理处理错误
- 7、监控调用链
- 十五、常见问题
- 1、多 Agent 一定比单 Agent 更强吗？
- 2、子 Agent 可以使用不同模型吗？
- 3、子 Agent 必须作为工具注册吗？

## 复习重点

- 能说明 `LangChain 多 Agent` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
