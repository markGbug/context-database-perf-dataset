# Claude Code：Claude Code Git 工作流

- 来源：[Claude Code Git 工作流](https://www.runoob.com/claude-code/claude-code-git-workflow.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：学习笔记
- 章节序号：0169

## 本章内容

Claude Code 深度集成了 Git 功能，可以用自然语言完成几乎所有 Git 操作，包括创建提交、管理分支、处理合并冲突，以及利用 Git Worktree 实现并行工作流。本章详细介绍如何在 Claude Code 中高效使用 Git。


## 基础 Git 操作


### 1、查看变更

用自然语言询问即可获取 Git 状态：

```text
我改了哪些文件？
```

```text
这次的改动有哪些内容？
```

```text
最近 10 次提交都改了什么？
```

```text
检查一下当前的 git 状态
```

Claude 会自动执行相应的 Git 命令并展示结果。


### 2、提交代码

简单提交：

```text
提交这次的改动
```

```text
把这次的修改提交
```

带描述的提交：

```text
把这次的修改提交，commit 信息说明修复了登录验证的 bug
```

Claude 会根据实际改动内容自动生成符合规范的 commit 信息。


### 3、分支管理

```text
新建一个 feature/user-profile 分支
```

```text
切换到 develop 分支
```

```text
把 main 分支的最新改动合并进来
```

```text
查看所有分支
```

```text
删除已合并的分支
```


## 处理合并冲突


### 1、自动解决简单冲突

```text
帮我解决合并冲突
```

```text
这个文件有冲突，帮我看看哪个版本是正确的
```

Claude 会分析冲突内容，根据项目上下文选择合适的版本或提出解决方案。


### 2、人工介入解决复杂冲突

当冲突过于复杂时，Claude 会向你说明各种选择的利弊：

```text
这个冲突涉及架构设计，你来决定保留哪个方案：
A. 保留我们的实现...
B. 保留引入的优化...
```

Claude Code 在执行任何文件修改前都会展示修改内容并请求你的确认。对于合并冲突这类高风险操作，更要仔细审查每个修改。


## Git Worktree 并行工作流

Git Worktree 允许你在不同目录中同时处理不同的分支，而无需切换分支或克隆仓库。这是 Claude Code 中最强大的并行工作方式之一。


### 1、使用 Claude 创建 Worktree

启动 Claude 时指定 worktree：

```text
claude --worktree feature-auth
```

这会自动：

- 在 .claude/worktrees/feature-auth/ 创建新目录
- 基于 origin/HEAD（远程默认分支）创建新分支
- 在新目录中启动独立 Claude 会话

同时开多个 worktree：

```text
claude --worktree bugfix-123
```

```text
claude --worktree
```

不指定名称时，Claude 会自动生成有趣的名字（如 bright-running-fox）。


### 2、Worktree 属性


### 3、Worktree 生命周期


### 4、复制 .gitignore 文件到 Worktree

在项目根目录创建 .worktreeinclude 文件，指定需要复制到 worktree 的 gitignore 文件：

```text
.env
.env.local
config/secrets.json
```

只有匹配某个模式 且 被 gitignore 的文件才会被复制。


### 5、手动管理 Worktree

如果需要更多控制，可以手动管理：

```text
# 创建 worktree 并指定分支
git worktree add ../project-feature-a -b feature-a

# 使用已有分支创建 worktree
git worktree add ../project-bugfix bugfix-123

# 在 worktree 中启动 Claude
cd ../project-feature-a && claude

# 完成后清理
git worktree list
git worktree remove ../project-feature-a
```

建议将 .claude/worktrees/ 加入 .gitignore，避免 worktree 内容在主仓库中显示为未跟踪文件。


## 子代理 Worktree 隔离

子代理可以使用 worktree 隔离功能，实现完全独立的并行工作：

方式一：让 Claude 自动处理

```text
让子代理使用 worktree 来并行处理这些任务
```

方式二：在子代理配置中指定


## 实例


### 子代理 Worktree 特点

- 每个子代理自动获得独立的 worktree
- 任务完成后自动清理 worktree
- 修改不会影响主仓库
- 适合探索性任务和方案对比


## Pull Request 工作流


### 1、创建 PR 的步骤

第一步：让 Claude 总结变更

```text
总结一下我对认证模块做的改动
```

第二步：生成 PR

```text
创建一个 PR
```

第三步：完善 PR 描述

```text
在 PR 描述中补充更多关于安全改进的内容
```


### 2、PR 会话关联

使用 gh pr create 创建 PR 时，Claude 会话会自动关联到该 PR：

- 会话链接到 PR 后，可以从 PR 恢复对话
- 使用 claude --from-pr <number> 恢复关联的会话


### 3、使用 GitHub CLI

Claude 了解如何使用 gh CLI 工具。如果没有安装 gh，Claude 可以读写 GitHub API，但功能有限。

```text
# Claude 可以执行的操作
gh pr create --title "Fix login bug"
gh pr view --comments
gh pr diff
gh issue create --title "Bug report"
```


## 会话管理与 Git 集成


### 1、恢复之前的会话


### 2、会话选择器 Git 功能


### 3、会话元数据显示

会话选择器显示以下信息：

- 会话名称或初始提示
- 上次活动距今时间
- 消息数量
- Git 分支（如果有）


## 后续章节

- 4、分支会话
- 计划模式与安全分析
- 启动计划模式
- 在 settings.json 中配置默认模式
- 实例
- 典型工作流示例
- 工作流一：多任务并行开发
- 工作流二：Bug 修复流程
- 工作流三：代码审查
- 工作流四：功能开发与验证
- 非 Git 版本控制系统
- 配置自定义钩子
- 实例
- Anthropic 内部团队最佳实践
- 常见问题

## 复习重点

- 能说明 `Claude Code Git 工作流` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
