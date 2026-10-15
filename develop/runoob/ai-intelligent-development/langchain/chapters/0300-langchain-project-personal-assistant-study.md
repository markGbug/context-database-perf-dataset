# LangChain：LangChain 多工具个人助手

- 来源：[LangChain 个人助手](https://www.runoob.com/langchain/langchain-project-personal-assistant.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：学习笔记
- 章节序号：0300

## 本章内容

前面我们已经介绍了 LangChain 的 Tools、Agent、Middleware、Structured Output、Streaming 和 Checkpointer。

本章节将这些能力组合起来，构建一个 多工具个人助手 Agent。

这个助手能够查询天气、查看日程、处理邮件请求，还可以根据天气和日程生成结构化的每日摘要，并记住同一会话中的聊天内容。

本项目基于 LangChain 1.x，使用 DeepSeek 聊天模型，并通过 SQLite 保存对话状态。

说明：天气、日程和邮件均为本地模拟功能。项目不会访问真实天气服务、Google Calendar 或邮件服务器，也不会实际发送邮件。


## 一、系统功能与架构

我们希望个人助手具备以下能力：


### 系统执行流程

```text
用户发送自然语言指令
            ↓
         LangChain Agent
            ↓
       Dynamic Prompt
            ↓
          模型判断
            |
    +-------+--------+
    |       |        |
    ↓       ↓        ↓
 天气工具  日程工具  邮件工具
    |       |        |
    |       |        ↓
    |       |     人工确认
    |       |        ↓
    +-------+--------+
            ↓
         模型回复
            ↓
      SqliteSaver 保存状态

每日摘要请求：
天气数据 + 日程数据
            ↓
      结构化摘要 Agent
            ↓
       DailySummary
            ↓
         Markdown
```

需要注意，主 Agent 可以自行决定调用哪些工具，但每日摘要使用单独的结构化生成步骤，不要求普通邮件查询也返回摘要对象。


## 二、环境准备

建议使用 Python 3.11 或更新的兼容版本。


### 创建虚拟环境

```text
python -m venv venv
```

Windows：

```text
venv\Scripts\activate
```

macOS / Linux：

```text
source venv/bin/activate
```


### 安装依赖

```text
python -m pip install -U langchain langchain-deepseek langgraph langgraph-checkpoint-sqlite pydantic python-dotenv
```


### 配置 API Key

创建 .env：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
```

本教程只需要 DeepSeek API Key，不需要额外配置 Embedding 服务，因为没有使用 RAG 向量检索。


## 三、准备模拟天气和日程

为了让读者不接入第三方天气和日历 API 也能测试，我们使用 Python 字典保存模拟数据。

与固定写死 2024 年日期不同，本例根据程序运行日期生成日程。


### 实例：模拟数据


## 实例

注意：这些天气数值只是固定测试数据，不能用于真实的出行、天气预警等决策。

正式项目需要接入实际天气 API，并保留数据时间、城市及来源。


## 四、工具一：天气查询

使用 @tool 定义天气工具。

工具接受城市名称，从模拟数据库中查询天气。


### 实例：get_weather


## 实例

例如：

```text
get_weather("杭州")
```

工具返回：

```text
杭州模拟天气：晴，温度 25°C，湿度 60%。
```

Agent 可以将这个结果转换成更自然的回答，但不能将模拟天气描述成真实的实时天气。


## 五、工具二：查询日程

第二个工具负责查询指定日期的日程。

如果用户没有提供日期，则默认查询今天。

日期使用标准格式：

```text
YYYY-MM-DD
```


### 实例：query_schedule


## 实例

如果查询今天，可能输出：

```text
2026-10-13 的模拟日程：
- 10:00 团队周会（1小时）
- 14:00 Python 学习（2小时）
```

这里的日期仅用于说明格式，实际程序会读取运行当天的日期。

注意：目前的日程工具只支持读取，不支持新增、删除和修改日程。后续可以继续添加 create_event、update_event 等工具。


## 六、工具三：模拟邮件发送

邮件发送属于有外部副作用的操作。

如果直接允许模型调用真实 SMTP 或邮件 API，可能出现误发邮件、收件人错误或敏感信息泄露等问题。

因此，本教程增加人工确认环节。

执行流程：

```text
用户要求发送邮件
        ↓
Agent 调用 send_email
        ↓
展示收件人、主题和正文
        ↓
interrupt() 暂停
        ↓
人工批准或拒绝
        ↓
模拟执行结果
```


### 实例：send_email


## 实例

这里有两个需要注意的地方。

第一：只有审批通过后，工具才返回批准结果。

第二：本示例不调用真实邮件 API，因此不能返回"邮件发送成功"或虚构邮件 ID。

如果要接入真实服务，应该在审批后调用邮件服务，并根据其实际响应确认发送状态。


## 七、动态提示词：注入日期和时区

用户可能会问：

```text
今天有什么安排？
明天下午有什么日程？
```

为了让模型正确理解"今天""明天"，我们可以通过 @dynamic_prompt 动态注入当前日期。

与在 messages 中反复添加 SystemMessage 不同，dynamic_prompt 在模型请求阶段构造系统提示词，不需要修改聊天历史。


### 实例：inject_date_context


## 实例

这里显式设置了时区，避免服务器使用不同时区时导致日期解释不一致。

正式应用可以通过可信 Runtime Context 传入用户时区，实现不同地区用户的个性化日期处理。


## 八、结构化输出：DailySummary

用户除了查询天气和日程，还可能希望得到一份每日摘要。

例如：

```text
帮我整理今天的天气和日程，给我一份今日安排。
```

如果只让模型输出自由文本，格式可能每次不同。

可以通过 Pydantic 定义统一的数据结构。


### 实例：DailySummary


## 实例

模型需要按照这些字段生成结构化数据。

例如：

```text
{
    "date": "2026-10-13",
    "city": "杭州",
    "weather_summary": "模拟天气：晴，25°C",
    "event_count": 2,
    "key_events": ["10:00 团队周会", "14:00 Python 学习"],
    "suggestion": "按计划参加会议和学习"
}
```

这比直接解析自由文本更容易用于前端展示、保存和程序处理。


## 后续章节

- 九、将结构化数据渲染为 Markdown
- 实例：to_markdown()
- 实例
- 十、为什么不在主 Agent 上设置全局 response_format？
- 实例：创建摘要 Agent
- 实例
- 十一、生成每日摘要
- 实例：generate_daily_summary()
- 实例
- 十二、使用 SqliteSaver 保存对话
- 实例：创建 Checkpointer
- 实例
- 十三、流式输出：展示 Agent 执行过程
- 实例：展示节点更新
- 实例
- 十四、完整代码：多工具个人助手

## 复习重点

- 能说明 `LangChain 个人助手` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
