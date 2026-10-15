# DeepSeek Harness：DeepSeek Harness 服务隔离与作用域

- 来源：[DeepSeek Harness 服务隔离](https://www.runoob.com/deepseek-harness/deepseek-harness-isolation-scope.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：学习笔记
- 章节序号：0232

## 本章内容

本章节我们将介绍同一个服务，怎么让不同插件组看到不同实例。

这背后是 Cordis 的 服务隔离（service isolation）与 agent 作用域（scope）机制。


## 服务隔离：isolate

cordis.yml 支持服务隔离：同一个服务可以有多个实例，不同插件组看到不同实例。

关键词是 isolate 配置，配合 group 插件把插件分成组。


## 实例

plugin-a 和 plugin-b 各自看到自己组内的 Bash 实例，互不影响。

group-a 的 Bash 命令超时 5 秒，group-b 的超时 60 秒，两边互不知道对方的存在。


## 为什么需要隔离

不同任务对同一能力的需求可能完全不同。

比如快速交互的任务希望 Bash 快速超时，而长任务希望给足时间。

隔离让同一份服务按组配置、按组生效，而不是全局一刀切。


## 作用域：scope

scope 是按 agent（智能体）划分的注册单位。

一项贡献（工具、提示词段、变量、限制、监听器）要么是全局的，要么归属于恰好一个 scope key。

带作用域的注册不会向下继承给 subagent。

子树行为通过 lineage 数据表达，而不是通过 scope 结构。


## shadowing：最具体者胜出

shadowing 是按 agent 定制 persona 和定制工具变体的机制。

一个带作用域的工具，仅在该 scope 内替换同名的全局工具；其它 agent 仍看到全局版本。


## restriction：过滤全局工具

restriction 用 tools.restrict 为单个 scope 过滤全局工具集合。

被过滤掉的全局工具既不进入提示词，也拒绝执行，与不存在的工具无法区分。

换句话说，restriction 让一个 scope 里的 agent 完全「看不见」某些全局工具，而不是在调用时再拒绝。


## 小结自测

isolate 让同一服务按组实例化，scope 按 agent 划分注册，shadowing 与 restriction 分别实现同名替换与全局过滤。

自测一下：

- isolate: { shell: true } 让 group-a 与 group-b 的 Bash 实例是什么关系？
- 带作用域的注册会不会继承给 subagent？
- shadowing 与 restriction 各自解决什么问题？


## 复习重点

- 能说明 `DeepSeek Harness 服务隔离` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
