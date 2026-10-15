# LangChain：LangChain 错误处理与调试

- 来源：[LangChain 错误处理](https://www.runoob.com/langchain/langchain-error-handling.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：练习笔记
- 章节序号：0302

## 本章内容

开发 LangChain Agent 时，程序不可能始终正常运行。

例如，模型 API 请求超时、工具参数不正确、知识库检索失败、Token 超限，或者 Agent 反复调用同一个工具，都可能导致程序异常。

如果缺少合理的错误处理机制，一个普通的网络故障就可能导致整个任务中断；而错误配置的重试机制，又可能让 Agent 重复发送邮件、创建订单或执行支付。

因此，构建可靠的 Agent 不仅需要让模型能够完成任务，还需要考虑 错误分类、异常捕获、自动重试、执行限制、日志调试和故障恢复。

本章节基于 LangChain 1.x，介绍常见错误排查、ModelRetryMiddleware、ToolRetryMiddleware、ToolErrorMiddleware、Debug 模式、Streaming 调试和生产环境最佳实践。


## 一、LangChain 常见错误类型

可以将 Agent 运行错误划分为以下几类：

不同类型的错误应该采用不同的处理策略。

例如：

- 网络超时：可以在满足条件时重试。
- API Key 错误：应该立即修复凭据。
- 工具参数错误：应该重新校验参数。
- 订单创建失败：必须先确认订单是否已经实际创建，不能直接重复调用。

核心原则：不是所有异常都应该重试。首先判断错误是否可能通过再次调用得到解决，以及重复执行是否安全。


## 二、环境准备

本教程使用 LangChain 1.x 和 DeepSeek 聊天模型。


### 安装依赖

```text
pip install -U langchain langgraph langchain-deepseek python-dotenv pydantic
```

创建 .env 文件：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
```

在 Python 中加载：


## 实例

建议始终在当前项目的虚拟环境中安装依赖，避免系统 Python 和虚拟环境中的包版本不一致。


## 三、ImportError：导入失败

LangChain 1.x 将不同功能拆分到多个 Python 包中。

例如，DeepSeek 模型使用：

```text
from langchain_deepseek import ChatDeepSeek
```

如果只安装了 langchain，而没有安装 langchain-deepseek，就可能出现：

```text
ModuleNotFoundError: No module named 'langchain_deepseek'
```

解决方式：

```text
python -m pip install -U langchain-deepseek
```


### 检查安装版本


## 实例

注意，升级 LangChain 版本后，某些旧教程的导入路径可能已经变化。

建议优先检查对应版本的官方 API，而不是继续使用旧版的 AgentExecutor、旧版 Chain 或已经迁移的导入方式。


## 四、API Key 与身份认证错误

如果模型服务返回身份认证错误，常见原因包括：

- .env 文件不存在或未成功加载。
- API Key 拼写错误。
- 凭据已经失效或被撤销。
- 当前 Key 无权访问指定模型。
- 配置了错误的服务商 API 地址。

可以先检查环境变量是否存在：


## 实例

不要直接输出完整 API Key，也不要把 Key 写入程序日志。

注意：认证失败通常不是临时网络故障，不应该进行大量自动重试。应先检查凭据、账号和模型访问权限。


## 五、模型超时与自动重试

调用大语言模型时，可能遇到网络抖动、请求超时、服务短暂不可用等问题。

LangChain 提供 ModelRetryMiddleware，可以在模型调用失败时进行有限次数的重试。

基本处理流程：

```text
调用模型
    ↓
  是否成功？
    ├── 是 → 返回结果
    │
    └── 否
         ↓
     是否属于可重试错误？
         ├── 否 → 立即处理失败
         │
         └── 是
              ↓
          等待退避时间
              ↓
            重新调用
              ↓
          达到重试上限后停止
```


### 实例：ModelRetryMiddleware


## 实例

这里使用：

```text
max_retries=2
```

表示首次调用失败后最多再重试两次。

因此，最多可能执行：

```text
首次调用
    ↓ 失败
第一次重试
    ↓ 失败
第二次重试
    ↓
成功或停止
```

总计最多三次尝试。

本示例将模型客户端的 max_retries 设为 0，是为了避免 SDK 内部重试和 Middleware 重试叠加，便于教学与排查。

注意：生产环境应根据实际模型服务商错误类型调整 retry_on，避免对认证、权限和永久性参数错误重复请求。


## 六、理解指数退避 Backoff

当大量客户端同时遇到服务故障时，如果所有请求都立即重试，可能进一步增加服务压力。

因此，重试中间件支持指数退避。

例如：

```text
initial_delay=1.0
backoff_factor=2.0
jitter=False
```

当重试次数允许时，等待时间大致为：

```text
第一次重试前：1 秒
第二次重试前：2 秒
第三次重试前：4 秒
```

如果开启：

```text
jitter=True
```

等待时间会增加随机扰动，避免多个客户端在完全相同的时间集中重试。


### 常用重试参数

其中 on_failure="error" 表示重试耗尽后继续抛出异常。

如果使用 on_failure="continue"，模型错误可能被转换为 AIMessage 返回，应用需要区分错误回复和正常业务结果。


## 七、ToolRetryMiddleware：工具调用重试

Agent 除了调用模型，还会调用数据库、搜索服务和其他外部 API。

例如，一个课程搜索工具可能因为网络问题暂时失败。

如果工具操作可以安全重复执行，可以使用 ToolRetryMiddleware。


### 实例：只重试临时工具故障


## 实例

如果模型调用了 search_course，第一次工具执行会触发模拟 ConnectionError。

中间件可以进行重试，第二次调用成功后，将结果交给模型。

这里通过 retry_on 明确只对指定的临时故障重试。

注意：示例中的全局 attempts 计数器只用于单进程教学测试，不适合真实的并发服务。


## 八、哪些工具不应该自动重试？

不是所有工具都适合使用 ToolRetryMiddleware。

特别是具有外部副作用的工具，例如：

- 发送邮件。
- 创建订单。
- 执行支付。
- 删除文件。
- 修改数据库记录。

假设订单创建工具发生超时：

```text
Agent → 创建订单
             ↓
        服务端已经创建成功
             ↓
        响应在网络中丢失
             ↓
        Agent 认为调用失败
             ↓
             重试
             ↓
        创建第二个订单
```

因此，不能简单地认为"工具抛出异常就表示业务操作没有成功"。

对于真实业务，应优先设计：

- 幂等请求 ID。
- 唯一业务流水号。
- 执行结果查询。
- 重复请求检测。
- 必要的人工审批。

建议：ToolRetryMiddleware 优先用于搜索、只读查询等适合重复执行的工具。涉及支付和删除等操作时，必须额外设计幂等保护。


## 九、ToolErrorMiddleware：处理工具错误

有些错误没有必要重试，但需要转换成模型可以理解的工具失败信息。

例如，用户输入的课程编号不合法。

这时可以使用 ToolErrorMiddleware。


### 实例：处理业务参数错误


## 实例

这里仅处理 ValueError。

其他没有明确处理的异常会继续抛出，避免掩盖真正的系统故障。

需要注意，工具内部主动抛出的 ValueError 与模型调用工具时发生的参数绑定、Pydantic 校验错误不一定经过完全相同的处理路径。

建议：生产环境应分别处理工具输入校验、业务异常和基础设施故障，不要简单地用一个 except Exception 吞掉所有错误。


## 十、组合 Retry 与 Error Middleware

当某个工具既可能发生网络故障，也可能发生业务参数错误时，可以将 Retry 和 Error Middleware 组合使用。

设计思路：

```text
工具调用
    ↓
ToolRetryMiddleware
    ↓
临时错误？
    ├── 是 → 有限次数重试
    └── 否 → 不重试
    ↓
ToolErrorMiddleware
    ↓
转换允许公开的业务错误
    ↓
Agent 获得工具结果
```

例如：


## 实例

这里将 ToolErrorMiddleware 放在外层，ToolRetryMiddleware 放在内层。

当可重试错误最终仍然失败时，异常可以继续传递给外层处理器。

但本例中的 handle_tool_error 只处理 ValueError，因此 ConnectionError 等错误仍会向外传播。

如果需要向用户展示"服务暂时不可用"，可以显式增加相应的异常处理逻辑。


## 十一、debug=True：开启 Agent 调试模式

LangChain 的 create_agent() 支持 debug=True。

开启后，底层图执行过程会输出更详细的调试信息，包括节点执行和状态更新等内容。


## 后续章节

- 实例：启用调试模式
- 实例
- 十二、stream_mode="updates"：查看执行步骤
- 实例：查看模型与工具调用
- 实例
- 十三、stream_mode="debug"：更详细的图调试
- 实例：查看 Debug 事件
- 实例
- 十四、工具调用无限循环
- 使用 ToolCallLimitMiddleware 限制工具调用
- 实例
- 十五、限制模型调用次数
- 实例：限制单次模型调用
- 实例
- 十六、GraphRecursionError：递归限制异常
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `LangChain 错误处理` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
