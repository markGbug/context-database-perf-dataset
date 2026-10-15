# LangChain：LangChain 提示词——System Prompt 与 Dynamic Prompt

- 来源：[LangChain 提示词](https://www.runoob.com/langchain/langchain-system-prompt.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：概念卡
- 章节序号：0282

## 本章内容

提示词（Prompt）是控制大语言模型行为的重要方式。

在 LangChain Agent 中，System Prompt 用于定义模型的角色、职责、回答风格和工具使用规则。

如果需要针对不同用户、不同任务或不同对话阶段调整提示词，还可以通过 @dynamic_prompt 动态生成系统提示。

本章节介绍 LangChain 1.x 的静态与动态提示词，并使用 DeepSeek Flash 模型进行演示。


## 一、System Prompt 基本用法

create_agent() 通过 system_prompt 参数接收系统提示词，支持字符串和 SystemMessage 两种常见形式。


### 方式一：使用字符串


## 实例

这种方式最简单，适合系统提示词相对固定的场景。


### 方式二：使用 SystemMessage


## 实例

SystemMessage 是 LangChain 的消息对象，可以在多个 Agent 或模型配置之间复用。

两种方式都用于设置系统提示词，通常选择字符串即可。

注意：System Prompt 可以影响模型行为，但不能保证模型始终严格遵守。涉及权限、支付和数据访问等操作，应由应用程序进行校验。


## 二、如何设计有效的 System Prompt？

好的系统提示词不一定很长，关键是让模型清楚自己的职责、能够使用哪些工具，以及遇到未知信息时如何处理。

一般可以包含五个部分：


### 实例：课程推荐助手


## 实例

如果模型正确调用工具，可能回答：

```text
可以先学习 Python3 基础教程，从变量、数据类型和基本语法开始。

这是演示课程数据，实际课程信息请以网站页面为准。
```

模型是否调用工具、最终回答的具体措辞并不固定。

建议让提示词尽量明确，避免同时提出相互矛盾的要求，例如既要求"详细解释"，又要求"只能回答一句话"。


## 三、@dynamic_prompt：动态生成系统提示词

静态 System Prompt 在不同调用之间保持相对固定，但实际应用可能需要根据当前任务动态修改。

例如：

- 初学者使用通俗易懂的解释。
- 高级开发者使用更专业的术语。
- 根据对话进度调整回答长度。
- 根据当前用户的学习目标提供建议。

LangChain 提供 @dynamic_prompt 装饰器，它是一种 Middleware，可以在每次模型调用前生成当前使用的系统提示。


### 基本语法

```text
from langchain.agents.middleware import dynamic_prompt, ModelRequest

@dynamic_prompt
def my_prompt(request: ModelRequest) -> str:
    return "你是一名编程助手。"
```

随后将其加入 create_agent() 的 middleware 参数：

```text
agent = create_agent(
    model="deepseek:deepseek-flash",
    middleware=[my_prompt]
)
```

@dynamic_prompt 接收 ModelRequest，返回 str 或 SystemMessage，作为当前模型请求的系统提示。


## 四、根据对话阶段动态调整提示词

可以通过 request.state 读取当前 Agent 状态，根据消息数量调整提示词。


### 实例：短对话与长对话


## 实例

首次调用时，消息较少，模型可能采用引导式回答：

```text
你好！你想学习 Python、Java 还是前端开发？
目前是否有编程基础？
```

当消息历史较长时，动态提示词会要求模型更加简洁。

注意：消息数量不等于对话轮数。一轮 Agent 执行可能产生 AIMessage、ToolMessage 等多条消息。

另外，如果没有配置 Checkpointer，多次独立 invoke() 不会自动共享上一轮的完整对话历史。


## 五、ModelRequest 提供哪些信息？

@dynamic_prompt 的参数是 ModelRequest，其中包含当前模型请求的相关信息。

其中，最常用的是 request.state 和 request.runtime.context。

注意：request.runtime.context 的数据结构由应用程序的 context_schema 决定，不能假设它始终是字典。


## 六、根据用户级别动态生成提示词

相比根据消息数量调整提示词，实际业务更常见的需求是根据用户信息进行调整。

例如，编程学习网站可以按照用户的学习等级提供不同的解释方式。

这里推荐使用 context_schema 定义运行时上下文，并由应用程序传入用户等级。


### 完整实例：不同等级的学习助手


## 实例

两次调用的问题相同，但提供了不同的用户等级。

模型因此可能采用不同的解释方式：

这里的 Context 由应用程序传入，不应该直接信任模型自己声称的用户身份或权限。


## 七、根据时间动态生成提示词

动态提示词也可以读取时间信息，例如用于不同时间段的问候语。

不过，服务器时间不一定与用户所在地时间相同，因此应明确使用哪个时区。


### 实例：按指定时区生成问候语


## 实例

这里显式使用 Asia/Shanghai 时区，避免依赖服务器操作系统的本地时区。

但它仍然只是北京时间，不一定是用户所在地时间。如果网站支持多时区，应从可信的用户设置中读取时区，并验证其有效性。

另外，@dynamic_prompt 在每次模型请求前执行，建议避免在函数中直接进行耗时的数据库扫描、大文件处理或复杂网络请求。


## 八、静态与动态 System Prompt 的关系

如果同时设置：

```text
create_agent(system_prompt=...)

middleware=[dynamic_prompt_function]
```

那么 @dynamic_prompt 返回的提示词会被用于当前模型请求。

因此，它可能替换原来的静态 System Prompt，而不是自动拼接在后面。


### 实例：动态提示词覆盖静态提示词


## 实例

此时模型请求使用的是动态函数返回的系统提示。

注意：如果存在多个修改系统提示词的 Middleware，最终效果还受到中间件的执行顺序及组合逻辑影响，不能简单套用一个固定的全局优先级。


## 九、将静态与动态提示词组合

实际项目中，通常希望保留一组固定规则，同时根据用户信息追加个性化内容。

推荐把公共规则单独定义，然后在动态提示词中组合。


## 后续章节

- 实例：公共规则 + 用户级别
- 实例
- 读取当前 system_prompt
- 实例
- 十、System Prompt 与工具调用
- 十一、完整实例：个性化编程学习 Agent
- 完整实例
- 十二、常见问题
- 1、System Prompt 与 HumanMessage 有什么区别？
- 2、@dynamic_prompt 每轮都会执行吗？
- 3、动态提示词可以返回 SystemMessage 吗？
- 4、如何读取用户等级？
- 5、Context 是字典还是对象？
- 6、动态提示词会自动保留静态提示词吗？
- 7、可以获取当前 System Prompt 吗？
- 8、为什么对话消息数量比实际轮数多？

## 记忆卡片

- 一句话定义：`LangChain 提示词` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
