# Pi Agent：Pi Agent 非交互模式

- 来源：[Pi Agent 非交互模式](https://www.runoob.com/pi-agent/pi-agent-non-interactive.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：概念卡
- 章节序号：0484

## 本章内容

除了交互式对话，Pi Agent 还提供了三种非交互模式，适用于脚本集成、自动化流程和程序间通信。


## Print 模式（-p）

Print 模式是最常用的非交互模式，执行一次性问答后输出结果并退出。


### 基本用法

最简单的形式是在 -p 后面直接跟一句提问，AI 回答完就退出。

```text
$ pi -p "帮我总结一下这个项目的结构"
这是一个 TypeScript + Vite 项目，源码集中在 src/ 目录下。
入口文件是 src/main.ts，工具函数位于 src/utils/，共 18 个模块。
```

用 @ 引用文件，让 AI 读取指定文件的内容：

```text
$ pi -p @README.md "这段文档的主要内容是什么"
这份 README 介绍了安装步骤、环境变量配置和三条常用命令。
```

用管道把命令输出直接喂给 AI，适合处理日志、文档等文本：

```text
$ cat README.md | pi -p "用三句话总结这段文字"
1. 项目要求 Node 20 以上版本。
2. 安装依赖后先把 .env.example 复制为 .env。
3. 日常调试用 npm run dev，发布构建用 npm run build。
```

@ 同样可以引用图片，让 AI 分析图像内容：

```text
$ pi -p @screenshot.png "图片中显示的错误信息是什么"
截图中的报错是 Module not found: Can't resolve './utils/format'，
说明 src/index.ts 里的相对路径拼写有误。
```

用 --name 给会话命名，之后可以在交互模式中接着这条线继续问：

```text
$ pi --name "快速审查" -p "审查 src/ 目录下的代码质量"
代码整体质量良好，有 3 处可以改进：
1. src/api/user.ts 缺少对分页参数的校验。
2. src/utils/format.ts 的日期格式化未处理时区。
3. src/db/query.ts 的裸抛异常建议补充错误码。
```


### 指定模型

用 --provider 加 --model 指定模型，也可以把两者合并写成 provider/model 的组合形式。

```text
$ pi --provider openai --model gpt-4o -p "帮我重构这段代码的逻辑"
重构建议：把 src/service/order.ts 中 120 行的 createOrder 拆成
校验参数、计算金额、落库三个函数，并为每个函数补充单元测试。
```

下面这种组合写法与上一条完全等价，写起来更短：

```text
$ pi --model openai/gpt-4o -p "帮我重构这段代码的逻辑"
```

模型名后加冒号和推理等级，可以控制这次调用的思考深度：

```text
$ pi --model sonnet:high -p "这个复杂的算法有什么潜在问题"
主要风险有三点：递归深度没有上限会导致栈溢出；
缓存键未包含用户身份，存在越权读取的可能；
批量写入缺少事务包裹，失败时会出现半提交状态。
```

--model 中的 :thinking 后缀（如 sonnet:high）与 --thinking 参数都能设定推理等级。

建议二选一，避免两处写法不一致时难以排查。

用 --models 限定可用的模型范围，多个模式之间用逗号分隔：

```text
$ pi --models "claude-*,gpt-4o" -p "审查代码"
审查完成：共发现 2 个阻塞问题和 5 个改进建议，
详细列表已按严重程度排序。
```


### 工具控制

通过命令行参数控制 AI 能使用哪些工具，是让非交互模式安全跑在脚本里的关键。

Pi Agent 在非 Windows 平台内置 7 个工具：read、write、edit、bash、grep、find、ls。

Windows 下 bash 由 powershell 替代。

用 --tools 做白名单，只保留指定工具，例如不改动任何文件的只读模式：

```text
$ pi --tools read,grep,find,ls -p "审查代码不修改"
审查结果：共 4 个问题，其中 1 个涉及并发写入，
完整报告已输出到终端，本次未修改任何文件。
```

用 --exclude-tools 排除指定工具：

```text
$ pi --exclude-tools bash -p "分析代码但不执行命令"
分析结论：该模块的性能瓶颈在循环内的重复文件读取，
建议把目录列表提到循环外，预计可减少 80% 的 I/O。
```

用 --no-builtin-tools 禁用全部内置工具，AI 只能基于对话内容回答，扩展和自定义工具仍然可用：

```text
$ pi --no-builtin-tools -p "纯问答"
Quicksort 的平均时间复杂度是 O(n log n)，
最坏情况是 O(n^2)，出现在已排序数组上选取首元素为主元时。
```

需要把扩展、自定义工具也一起禁用时，改用 --no-tools。


## JSON 模式（--mode json）

JSON 模式将所有事件以 JSON 行（JSONL）格式输出，适合程序解析和处理。

```text
$ pi --mode json "总结项目结构"
{"type":"session","version":3,"id":"019f8c2e-7a41-7b3d-9e5f-2c6a1d84b0e7","timestamp":"2026-08-31T02-40-11-000Z","cwd":"/Users/runoob/projects/runoob-demo"}
{"type":"agent_start"}
{"type":"turn_start"}
{"type":"message_start","message":{...}}
{"type":"message_update","usage":{...},"assistantMessageEvent":{...}}
{"type":"message_end","message":{...}}
{"type":"turn_end","message":{...},"toolResults":[]}
{"type":"agent_end","messages":[...]}
```

首行是会话元数据头，记录格式版本、会话 ID、时间戳和工作目录。

之后的每一行都是一个独立的 JSON 事件，包含事件类型和对应的数据。

这种模式适合以下场景：


## RPC 模式（--mode rpc）

RPC 模式通过 stdin/stdout 的 JSONL 协议实现进程间通信。

它允许另一个程序通过标准输入发送命令，并从标准输出读取响应。

RPC 模式支持扩展 UI 协议，使远程客户端能够呈现 confirm 对话框、选择列表等交互元素。

这种模式适合以下场景：

RPC 模式和 JSON 模式是面向开发者的高级特性。

作为初学者，你大概率只需要交互模式和 Print 模式。

当你需要将 Pi Agent 集成到工具链中时，可以再回来深入学习这两种模式。


## 模式对比

三种非交互模式的差异主要体现在交互性和输出格式上，按下表选择即可。


## CLI 参数速查

下表按用途归类列出 pi 命令的常用参数，可与交互模式中的命令互相配合。


## 记忆卡片

- 一句话定义：`Pi Agent 非交互模式` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
