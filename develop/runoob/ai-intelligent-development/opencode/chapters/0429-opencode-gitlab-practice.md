# OpenCode：OpenCode GitLab

- 来源：[OpenCode GitLab](https://www.runoob.com/opencode/opencode-gitlab.html)
- 分类：AI / 智能开发
- 技术：OpenCode
- 笔记类型：练习笔记
- 章节序号：0429

## 本章内容

OpenCode 同样可以集成到 GitLab 工作流中，在 Issue、合并请求（Merge Request）以及 CI/CD 流水线中自动执行任务。

它的核心特点是：在你的 GitLab Runner 上运行，实现安全可控的 AI 自动化开发。

OpenCode GitLab = 把 AI 接入 CI/CD，让代码分析、修复和审查自动化运行。


## 一、集成方式概览

OpenCode 在 GitLab 中主要有两种使用方式：

- GitLab CI（推荐）：通过 CI/CD 流水线执行 OpenCode
- GitLab Duo（评论触发）：通过 @opencode 在评论中触发


## 二、GitLab CI 集成（核心方式）

OpenCode 可以作为 CI 组件接入你的流水线，实现自动化任务执行。

这里使用社区组件：

```text
nagyv/gitlab-opencode
```


### 1、功能特性

- 按任务自定义配置：支持独立配置目录
- 最小化接入成本：无需复杂初始化
- 高度可定制：支持多参数控制行为


### 2、配置步骤

在 GitLab 项目中：

- 进入 Settings → CI/CD → Variables
- 添加变量：

```text
OPENCODE_AUTH_JSON
```

要求：

- 类型：File
- 勾选 Masked 和 Hidden

在项目根目录创建或修改：

```text
.gitlab-ci.yml
```

示例：

```text
include:
  - component: $CI_SERVER_FQDN/nagyv/gitlab-opencode/opencode@2
    inputs:
      config_dir: ${CI_PROJECT_DIR}/opencode-config
      auth_json: $OPENCODE_AUTH_JSON
      command: optional-custom-command
      message: "Explain the codebase structure"
```


### 3、使用场景

- 自动分析代码结构
- 批量重构代码
- 自动生成文档
- CI 阶段自动检查代码质量


## 三、GitLab Duo 集成（评论触发）

类似 GitHub 的 /opencode，GitLab 使用 @opencode 触发。

当你在 Issue 或合并请求中评论时：

```text
@opencode your prompt
```

OpenCode 会在 GitLab CI 中自动执行任务


### 1、功能特性

- Issue 分析：自动理解问题
- 自动修复：创建分支并提交 MR
- 代码审查：分析合并请求

特点：

- 运行在 GitLab Runner 上
- 安全，不依赖外部执行环境


### 2、配置步骤

要使用 @opencode，需要完成以下配置：

- 配置 GitLab CI/CD 流水线
- 准备 API Key
- 创建服务账户（Service Account）
- 配置 CI/CD Variables
- 创建 Flow 配置文件

说明：

具体细节可参考 GitLab CLI Agents 官方文档（不同版本略有差异）。


## 四、常见使用方式


### 1、解释 Issue

```text
@opencode explain this issue
```

自动总结问题并给出解释


### 2、自动修复 Issue

```text
@opencode fix this
```

自动：

- 创建新分支
- 修改代码
- 提交 Merge Request


### 3、审查合并请求

```text
@opencode review this merge request
```

自动分析：

- 代码质量
- 潜在 Bug
- 优化建议


## 五、进阶技巧


### 1、自定义触发词

你可以将 @opencode 替换为其他触发关键词。


### 2、任务级配置

通过不同的 config_dir，实现：

- 不同任务使用不同模型
- 不同项目使用不同规则


### 3、结合 CI 自动化

可以实现：

- 定时扫描代码问题
- 自动生成周报
- 自动修复简单 Bug


## 六、安全与最佳实践

- 使用 CI/CD Variables 存储密钥
- 避免在代码中写死 API Key
- 合理控制 Runner 权限
- 限制自动修改代码的范围


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `OpenCode GitLab` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
