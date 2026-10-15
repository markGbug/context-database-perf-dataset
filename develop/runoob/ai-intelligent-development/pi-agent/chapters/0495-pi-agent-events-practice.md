# Pi Agent：Pi Agent 事件系统

- 来源：[Pi Agent 事件系统](https://www.runoob.com/pi-agent/pi-agent-events.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：练习笔记
- 章节序号：0495

## 本章内容

事件系统是扩展的核心机制。

通过监听生命周期事件，你可以在 AI 工作的各个阶段插入自定义逻辑。


## 生命周期全景

以下是 Pi Agent 从启动到退出过程中触发的所有事件：

每个 turn 内部，context、provider、tool 三类事件按序触发，有工具调用时循环多轮。

虚线部分表示该阶段可被多个事件多次触发。

input、before_agent_start、resources_discover、agent_settled 等其余事件的触发时机见下方全事件速查表。


## 核心事件详解

这一节挑选使用频率最高的 5 个事件，说明它们的触发时机和返回值约定。


### input — 输入拦截

在用户输入被处理之前触发，可以转换、拦截或直接处理输入：


## 实例

两种典型写法的实际效果如下。

输入 ?quick hello world 时，实际发给 LLM 的文本已被改写：

```text
简短回复：hello world
```

输入 ping 时不会调用 LLM，终端里只弹出一条通知：

```text
pong
```

input 事件在 Skill 和模板展开之前触发，所以你看到的是原始输入。

/skill:foo 和 /template 此时尚未展开。


### tool_call — 工具调用拦截

在工具执行之前触发，可以修改参数或阻止执行：


## 实例

若 AI 试图执行 rm -rf /，工具不会运行，终端中会显示阻断原因：

```text
危险命令已被阻止
```

event.input 是可变的——你修改它会直接影响工具执行。


### tool_result — 修改工具结果

在工具执行完成后触发，可以修改返回给 LLM 的结果：


## 实例

原本两行的文件内容，交给 LLM 时会变成带行号的形式：

```javascript
1: import { readFile } from "node:fs/promises";
2: export async function load() {
```


### context — 修改 LLM 上下文

在每次 LLM 调用之前触发，可以过滤或修改消息：


## 实例


### before_agent_start — 注入消息

在 AI 开始处理用户输入之前触发，可以注入额外消息或修改系统提示词：


## 实例


## 全事件速查表

上一节的 ASCII 图里还出现了不少事件，这里按触发顺序集中列出，方便查阅。


## 事件处理要点

写事件 handler 时，下面这几点决定了代码是否健壮。

在扩展工厂函数中不要启动后台资源（进程、socket、定时器等）。

将资源启动延迟到 session_start 事件中，并在 session_shutdown 中清理。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pi Agent 事件系统` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
