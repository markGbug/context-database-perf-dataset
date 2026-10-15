# DeepSeek Harness：DeepSeek Harness 能力三角色：Definition / Provider / Consumer

- 来源：[DeepSeek Harness 能力三角色](https://www.runoob.com/deepseek-harness/deepseek-harness-capability-seams.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：练习笔记
- 章节序号：0234

## 本章内容

官方文档里经常出现 Service Definition、Service Provider、Consumer 这三个词，它们合在一起构成一项能力的 seam，也就是可替换的能力接口。

本章节将讲清楚三者分别是什么，以及为什么要把一个能力拆成三个角色。

完整能力构成其 seam；任何单一角色都不是 seam。


## 三种角色各是什么

当一项能力足够通用、需要支持可替换的提供方时（例如 Bash 执行），harness 会把能力拆成三种角色。

Service Definition 只声明「有什么能力、长什么样」，不关心怎么实现。

Service Provider 继承 Definition 的抽象类，填上具体行为。

Consumer 面向模型，把能力包装成工具 schema，让模型能够调用。

三个角色可以放在同一个包里，也可以拆进不同包。

判断标准只有一个：这些角色是否需要独立演进或替换。


## 一张图看懂 seam 三角色

三个角色都依赖 Definition，而 Provider 与 Consumer 互不依赖。

图中的虚线框就是完整能力，也就是 seam。

Definition 在中间，Provider 与 Consumer 都只依赖它。

Provider 继承实现 Definition，Consumer 通过 inject: ['shell'] 依赖它。

Provider 与 Consumer 之间没有任何依赖。

因此换 Provider 时，Definition 和 Consumer 一行都不用改。


## 以 Bash 为例：ctx.shell 的三角色

Bash 执行是 dsh 里最典型的一个 seam，三个角色各有一个包。

Service Definition 是 dsh-shell 包，注册为 ctx.shell 服务。

它定义 Bash 的请求类型 ShellExecRequest 和结果类型 ShellRunResult。

Service Provider 是 dsh-bash-local，在本地计算机上执行命令。

同一份 Definition 还有其它 Provider，例如 dsh-bash-sandbox 在沙箱里执行，dsh-pwsh-local 执行 PowerShell。

Consumer 是 dsh-tool-bash，把能力包装成模型可调用的 bash 工具。

tool-bash 通过 inject 声明依赖 ctx.shell，再在 execute 里调用 ctx.shell.run(...)。

官方《能力 Seam 与核心服务》参考文档用一张表维护了 ctx.shell 的三角色归属。

消费方还包括 hooks-claude-code 与 hooks-codex 这两个钩子桥接插件。

它们和 tool-bash 一样，只认 ctx.shell 这个接口，不关心背后是哪个执行器。

在 Bash seam 里，面向模型的请求 ShellExecRequest（workdir、timeoutMs 可选）与执行器实际使用的完全解析后的规格 ShellExecSpec（字段必填）被分开。

工具层在二者之间调用 ctx.shell.resolve(request)，这就是「包边界处显式优于隐式」。


## 为什么要拆成三个角色

拆分的第一个好处是提供方可替换。

同一个 Service Definition 可以有多个提供方，通过 cordis.yml 选择。


## 实例

更换提供方时，Service Definition 和 Consumer 均保持不变。

拆分的第二个好处是三个角色可以独立演进。

拆分的第三个好处是依赖解耦。

Service Provider 依赖 Service Definition。

Consumer 依赖 Service Definition。

Service Provider 和 Consumer 互不依赖。


## 动手梳理：找到你正在用的 seam 的三角色

官方《能力 Seam 与核心服务》参考文档维护着一张完整的服务清单。

挑一个你熟悉的 seam，例如 ctx.fs 或 ctx.llm，按三步梳理即可。

第一步，找出它的 Definition 包，也就是表格里「所属包」那一列。

第二步，找出它的 Provider 包，也就是表格里「实现」那一列。

第三步，找出它的 Consumer，也就是表格里「直接消费方」那一列。

例如 ctx.llm 的 Definition 是 llm 包，实现是 llm-deepseek 与 llm-pi-ai，直接消费方是 agent-loop 与 compaction-basic。

再例如 ctx.fs 的 Definition 是 fs 包，实现是 fs-local、fs-sandbox 与 fs-e2b，直接消费方是 tool-fs。

习惯了这个思路之后，再看任何内置服务，你都能一眼分清它属于哪个角色。


## 小结与自测

一句话总结：能力被拆成 Definition（接口与类型）、Provider（实现）、Consumer（面向模型的工具）三个角色，三者合起来才是 seam。

自测题一：Bash 能力的 Definition、Provider、Consumer 分别对应哪个包？

自测题二：更换 Bash 的 Provider 时，哪些包可以保持不变？

自测题三：为什么说「任何单一角色都不是 seam」？


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `DeepSeek Harness 能力三角色` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
