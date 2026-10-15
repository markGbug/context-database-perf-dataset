# LangChain：LangChain 人工介入——Human-in-the-Loop（HITL）

- 来源：[LangChain 人工介入](https://www.runoob.com/langchain/langchain-human-in-the-loop.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：练习笔记
- 章节序号：0293

## 本章内容

在实际的 AI Agent 应用中，并不是所有操作都适合交给模型自动执行。

例如，发送邮件、删除数据、修改数据库、执行支付等操作，可能对真实业务产生影响，因此通常需要人工确认。

LangChain 提供 Human-in-the-Loop（HITL，人工介入） 机制，让 Agent 在执行关键操作前暂停，等待人工审批，再决定继续、修改或取消。

本章节基于 LangChain 1.x 和 LangGraph，介绍 interrupt()、Command(resume=...)、HumanInTheLoopMiddleware、静态中断点以及 Web 审批架构。


## 一、什么是人工介入 HITL？

Human-in-the-Loop 指的是在 AI 自动化流程中保留人工决策环节。

例如，一个管理员要求 Agent 删除课程：

```text
管理员：删除《过时的 Java 教程》
           ↓
       Agent 理解任务
           ↓
       准备执行删除工具
           ↓
        暂停执行
           ↓
    人工查看操作内容
           ↓
       ┌───────────────┐
       │               │
     批准             拒绝
       │               │
    执行删除         取消删除
       │               │
       └───────┬───────┘
               ↓
          返回最终结果
```

HITL 的作用不是让模型自己判断"是否获得了授权"，而是让外部可信系统真正参与决策。

常见场景包括：


## 二、LangChain 的三种中断机制

LangChain 和 LangGraph 主要提供三种人工介入方式。

对于大多数需要审核工具调用的 Agent，推荐优先使用 HumanInTheLoopMiddleware。

如果需要更复杂的自定义业务流程，可以直接使用 interrupt()。


## 三、interrupt()：动态暂停执行

interrupt() 是 LangGraph 提供的动态中断函数。

执行到该函数时，图会暂停，并向外部调用方返回审批或输入请求。

基本写法：

```text
from langgraph.types import interrupt

decision = interrupt({
    "action": "delete_course",
    "message": "确认删除课程？"
})
```

外部系统收到中断信息后，由人工做出决定。

随后通过：

```text
Command(resume={"approved": True})
```

恢复执行。


### interrupt() 的必要条件

正常使用需要三个关键要素：

- 一个 Checkpointer，用于保存暂停时的执行状态。
- 一个稳定的 thread_id，用于恢复正确的会话。
- 一个可序列化的中断数据，用于向外部显示审批内容。

重要：恢复时会重新执行包含 interrupt() 的节点，直到再次执行到对应的 interrupt()，才会得到之前通过 resume 传入的值。

因此，不应在 interrupt() 之前执行有不可重复副作用的操作。


## 四、在工具中使用 interrupt()

下面创建一个模拟课程删除工具。

工具会先暂停并申请批准，只有审批通过才执行模拟删除逻辑。


### 实例：模拟删除课程审批


## 实例

这里的中断请求包含操作类型、课程名称和提示信息。

恢复时传入：

```text
{"approved": True}
```

表示人工批准。

传入：

```text
{"approved": False}
```

则取消操作。

注意：以上仅是教学模拟。真实删除工具必须在执行时再次检查操作者权限，并使用可信后端完成数据库操作。


## 五、完整实例：暂停、审批、恢复

接下来将工具接入 Agent，完成一次完整的 HITL 流程。

安装依赖：

```text
pip install -U langchain langgraph langchain-deepseek python-dotenv
```

配置 .env：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
```

文件名：hitl_interrupt_demo.py


## 完整实例


### 可能的运行结果

```text
等待人工审批： {'action': 'delete_course', 'course': '过时的 Java 教程', ...}

执行结果： 已模拟删除《过时的 Java 教程》。
```

这里分为两个阶段：

第一阶段：Agent 执行到 interrupt()，返回待审批信息。

第二阶段：外部程序使用相同的 thread_id，并通过 Command(resume=...) 恢复执行。

示例使用 result["__interrupt__"] 检查中断，这是普通 invoke() 返回结构中的常见方式。

需要注意，工具是否被模型调用由模型决定。即使用户明确提出删除任务，实际运行也可能没有触发工具。


## 六、查看 Agent 的中断状态

当 Agent 暂停后，可以通过 get_state() 查看线程当前状态。


### 实例


## 实例

如果工具节点触发了中断，state.next 可能包含：

```text
('tools',)
```

表示图仍有待继续执行的工具节点。

注意：不应该假设 state.tasks[0] 必然对应当前审批，也不应该将所有暂停一律认定为工具审批。

真实应用应遍历待处理任务，结合中断 ID、线程及业务记录管理审批状态。


## 七、HumanInTheLoopMiddleware：内置工具审批

LangChain 1.x 提供 HumanInTheLoopMiddleware，可以在模型请求执行敏感工具时自动暂停，并等待人工审核。

它比在每个工具中手动调用 interrupt() 更方便，特别适合大量工具的统一审批管理。

主要支持四种决策：

其中 respond 主要适合等待用户回答的工具，例如 ask_user。

注意：不要使用 respond 拒绝删除或支付工具，因为它会生成成功的工具结果，可能让模型错误认为操作已经完成。


## 八、完整实例：HumanInTheLoopMiddleware

下面创建一个模拟课程删除 Agent，通过内置 Middleware 进行审批。


## 完整实例

这里使用 version="v2"，因此返回的是包含 value 和 interrupts 的执行结果对象。

它与不指定 v2 时通过 result["__interrupt__"] 读取中断信息的方式不同。

这一示例中：

- delete_course：必须审批。
- search_course：无需审批。
- approve：批准执行原工具调用。
- reject：拒绝执行并把拒绝反馈交给 Agent。

示例为简化演示，假定只有一个待审批动作。如果同时存在多个动作，需要针对每个动作分别提供决策。


## 九、批准、拒绝与修改工具参数

HumanInTheLoopMiddleware 的审批结果通过 Command(resume=...) 传递。


### 1、批准

```text
Command(resume={
    "decisions": [{"type": "approve"}]
})
```

表示按原始参数执行工具。


### 2、拒绝

```text
Command(resume={
    "decisions": [{
        "type": "reject",
        "message": "管理员不同意删除该课程，请勿再次尝试。"
    }]
})
```

被拒绝的工具不会执行，Agent 会获得对应的拒绝反馈。


### 3、编辑参数

如果允许人工修改工具调用，可以配置：

```text
"delete_course": {
    "allowed_decisions": ["approve", "edit", "reject"]
}
```

恢复时：

```text
Command(resume={
    "decisions": [{
        "type": "edit",
        "edited_action": {
            "name": "delete_course",
            "args": {"course_name": "指定的新课程名称"}
        }
    }]
})
```

这允许审批人修改工具参数。

注意：修改工具名称或参数可能改变实际业务操作，应由可信后端再次检查编辑后的工具、目标对象和审批人权限。

对于删除、支付等高风险操作，通常不建议允许审批人任意切换工具类型。


## 十、多个工具同时需要审批

Agent 可能在一次模型响应中请求调用多个工具。

例如：

```text
delete_course("旧版 Java 教程")
delete_course("旧版 PHP 教程")
```

如果两个工具调用都需要审批，HITL Middleware 可以返回多个待审核动作。

此时必须为每个动作提供对应决定。


### 实例：批量审批


## 实例

其中 decisions 的排列顺序必须与中断信息中 action_requests 的顺序一致。

不能只根据工具名称假设只有一个需要审批的请求。

实际 Web 系统还应记录每个审批动作的唯一 ID，确保审批人不会误批其他工具调用。


## 十一、interrupt_before 与 interrupt_after

除了动态中断，还可以通过 create_agent() 的参数在指定图节点前后设置静态中断点。

例如：


## 后续章节

- 实例
- 静态断点如何继续执行？
- 十二、动态中断与静态中断的区别
- 十三、恢复执行时的重要注意事项
- 错误示例
- 正确思路
- 十四、Web 应用中的 HITL 架构
- 实例：提交任务与读取审批状态
- 实例
- 实例：审批后恢复
- 实例
- 十五、HITL 与 Checkpointer
- 十六、HITL 的生产环境安全设计
- 1、审批操作必须由可信后端完成
- 2、审批对象必须绑定具体操作
- 3、审批后仍要再次验证权限

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `LangChain 人工介入` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
