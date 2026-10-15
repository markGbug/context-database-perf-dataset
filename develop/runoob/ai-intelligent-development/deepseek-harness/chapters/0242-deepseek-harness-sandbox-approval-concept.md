# DeepSeek Harness：DeepSeek Harness 沙箱与审批：让 Agent 危险动作可控

- 来源：[DeepSeek Harness 沙箱与审批](https://www.runoob.com/deepseek-harness/deepseek-harness-sandbox-approval.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：概念卡
- 章节序号：0242

## 本章内容

上一章节讲了工具执行流水线，其中两个环节最让人关心：沙箱怎么约束命令，审批怎么决定「能不能做」。

本章节将深入 ctx.sandbox 与 ctx.approval 两个服务，讲清它们各自的分工与故障关闭原则。

一句话：沙箱管「命令跑在什么边界里」，审批管「这个具体操作是否被允许」，两者都默认失败关闭。


## 先看整体：沙箱决策 + 审批流程

下面的图把两个服务放在一起看：左边是沙箱如何包装 argv，右边是审批如何做出一次性决策。

它们共同回答了同一个问题：Agent 想做一件有风险的事，怎么把它约束住。

沙箱把「进程能碰哪些文件」圈起来，审批把「是否放行这一次操作」交给应答者决定。


## ctx.sandbox：按策略包装 argv

进程沙箱的模型是：消费方交出确切的 argv，后端按文件效果策略把它包装起来。

关键点是「确切 argv」而不是 shell 字符串——一个 shell 形态的消费方要传 ['bash', '-c', command]。

ctx.sandbox.confine(argv, policy) 返回一个 ConfinedArgv，也就是「替换后的 argv 加上后端的强制执行事实」。

SandboxMode（沙箱模式）只管控文件系统效果，不含网络与进程可见性。

read-only：只允许必需的数据接收端（如 /dev/null），拒绝写入。

workspace-write：还允许在工作区根目录及后端承诺的临时区域下写入。

danger-full-access：绕过隔离，消费方直接 spawn 原始 argv，不调用 ctx.sandbox。

只有前两种模式会发给提供方，danger-full-access 根本不进沙箱。

这就保证了一个安全性质：受限执行必然到达 ctx.sandbox，静默的无隔离透传永远不合法。


## 强制执行程度与回退规则

后端报告它实际达成的强制执行完整度：enforcement: 'full' | 'partial'。

full 表示后端管控了该模式承诺的所有文件效果；partial 表示只管控了子集。

当前的部分强制执行情形包括较旧的 Landlock ABI，以及 Windows ACL runner 的 Everyone 与硬链接边界。

要求绝对边界的消费方必须把 partial 当作「不够」处理，拒绝或向上暴露这一区别。

策略的解析有明确的回退顺序，官方文档把它归纳为三层：

普通工具调用从调用会话的不可变 cwd 派生 workspaceRoot。

root 会先按文件系统语义规范化，再做词法规范化，因此包含 symlink/.. 的 cwd 会标识进程实际运行的目录。

故障关闭：当没有可用后端时，ctx.sandbox.confine 会抛出 SandboxUnavailableError，错误码 SANDBOX_UNAVAILABLE。

受限策略下，静默的无隔离透传永远不合法。


## 动手示例：受限模式下跑一次 bash

用代码把「沙箱化 bash」的调用路径串起来看看。


## 实例

说明：上面代码是演示性质的参考写法，省略了 spawn 与收集输出的细节。

生产级的消费方是 dsh-bash-sandbox，它同时负责 spawn 与结果归因。

真正的难点在结果分类：要把「沙箱 runner 失败」与「沙箱正常工作但拒绝」区分开。

沙箱还带回两种正交的 stderr 分类器：

denialSignatures：识别沙箱正常工作时、受限命令被阻止的情况（bwrap 的 EROFS 文本、Landlock 的 EACCES、Seatbelt 的 EPERM）。

runnerFailureRules：识别 runner 在执行命令之前拒绝或失败的情况（Landlock 失败要求退出码 125 加一行致命诊断）。

消费方应先把 runner 失败作为沙箱基础设施故障上报，而不是普通任务失败。


## ctx.approval：一次性权限决策

审批服务回答一个很窄的问题：这个具体操作是否可以继续？

它通过 approval/request waterfall 把问题分发给应答者（answerer）。

应答者在负责处理该请求时返回结果，否则调用 next() 委托；第一个应答者占据唯一的决策槽位。

结果类型 ApprovalOutcome 是闭合的：

关键安全性质：缺失、不负责该请求、抛异常或不合规的应答者都会产生 unavailable，而不是放行。

调用方对 rejected、cancelled 和 unavailable 一律执行拒绝。


## 按会话审批策略：ask 与 never

ApprovalPolicy 决定在交互式应答者运行之前发生什么。

生效值是会话日志中最后一条 approval/policy 事件，回退到服务配置。

setApprovalPolicy(session, policy) 是唯一的写入路径，因此回放能重建覆盖值。

never 在服务内部、waterfall 分发之前强制执行，所以即使后来用 prepend 注册的应答者也无法绕过它。

审计与模型可见性的区别：审批的审计事件对（approval/asked 与 approval/decided）只写日志，不进入模型 transcript。

模型可见的行为是调用方派生的工具结果与当前运行时上下文快照。


## 权限预设：两个 knob 捆绑成具名预设

沙箱模式（sandbox/mode）与审批策略（approval/policy）是两个相互独立的 knob。

权限预设层 ctx.permissionPresets 把它们捆绑成具名预设，供客户端作为单个「权限」选择器提供。

预设表是配置驱动的，默认表自带上面两个；名字 custom 被保留给「派生的非预设状态」。

current(events) 从两个 knob 折叠实际生效的预设，而不只是看预设自己的事件。

两个预设共享同一个 knob 组合时，permission/preset 事件让 current() 仍能保住用户选的究竟是哪一个。

重要：权限预设只描述它实际管辖的能力。

官方事故复盘 0002 就提醒过：组合时的文件系统访问无法安全地跟随运行时的 bash-only 预设。

在 runoob 生产环境里，danger-full-access 只应配给一次性、可丢弃的沙箱环境。


## 小结自测

沙箱与审批把「能力边界」与「决策授权」分开：沙箱用文件效果策略包装 argv，审批用瀑布式应答者做一次性放行。

自测题：


## 记忆卡片

- 一句话定义：`DeepSeek Harness 沙箱与审批` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
