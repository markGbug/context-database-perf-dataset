# Claude Code：Claude Code GitHub Actions

- 来源：[Claude Code GitHub Actions](https://www.runoob.com/claude-code/claude-code-github-actions.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：学习笔记
- 章节序号：0170

## 本章内容

Claude Code GitHub Actions 将 AI 驱动的自动化带到你的 GitHub 工作流中。

通过在 PR 或 Issue 中简单地提及 @claude，Claude 就可以分析代码、创建 Pull Request、实现功能、修复 Bug，同时遵循你项目的标准规范。


## 为什么使用 Claude Code GitHub Actions

- 即时创建 PR：描述你的需求，Claude 即可创建完整的 Pull Request
- 自动化代码实现：将 Issue 转化为可工作的代码，只需一条命令
- 遵循项目标准：尊重你的 CLAUDE.md 指南和现有代码模式
- 简单快速：几分钟内即可开始使用
- 安全可靠：代码保留在 GitHub 的 runner 上运行


## 快速开始


### 方式一：自动安装（推荐）

在 Claude Code 终端中运行：

```text
/install-github-app
```

这会引导你完成：

- 设置 GitHub App
- 添加必要的 Secrets

要求：你必须是仓库管理员。GitHub App 需要 Contents、Issues 和 Pull requests 的读写权限。仅适用于直接使用 Claude API 的用户（不支持 AWS Bedrock 或 Google Vertex AI）。


### 方式二：手动安装

访问：https://github.com/apps/claude

需要的权限：

- Contents：读写权限
- Issues：读写权限
- Pull requests：读写权限

在仓库 Secrets 中添加 ANTHROPIC_API_KEY

从示例文件复制：examples/claude.yml 到 .github/workflows/


## 工作流配置


### 基础工作流（响应 @claude 提及）

```text
name: Claude Code
on:
  issue_comment:
    types: [created]
  pull_request_review_comment:
    types: [created]
jobs:
  claude:
    runs-on: ubuntu-latest
    steps:
      - uses: anthropics/claude-code-action@v1
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
```


### 自动代码审查

```text
name: Code Review
on:
  pull_request:
    types: [opened, synchronize]
jobs:
  review:
    runs-on: ubuntu-latest
    steps:
      - uses: anthropics/claude-code-action@v1
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
          prompt: "Review this pull request for code quality, correctness, and security."
          claude_args: "--max-turns 5"
```


### 定时任务

```text
name: Daily Report
on:
  schedule:
    - cron: "0 9 * * *"
jobs:
  report:
    runs-on: ubuntu-latest
    steps:
      - uses: anthropics/claude-code-action@v1
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
          prompt: "Generate a summary of yesterday's commits and open issues"
          claude_args: "--model opus"
```


## @claude 常用命令

在 PR 或 Issue 评论中使用：

```text
@claude implement this feature based on the issue description
```

```text
@claude how should I implement user authentication for this endpoint?
```

```text
@claude fix the TypeError in the user dashboard component
```

```text
@claude review this PR for security issues
```

```text
@claude add tests for this new function
```


## Action 参数详解

*当在 issue/PR 评论中使用时省略 prompt，Claude 会响应触发词

**直接使用 Claude API 时必填，Bedrock/Vertex 时不需要


### 常用 CLI 参数


### claude_args 示例

```text
claude_args: |
  --max-turns 5
  --model claude-sonnet-4-6
  --mcp-config /path/to/config.json
  --append-system-prompt "Follow our coding standards"
```


## AWS Bedrock 集成


### 前置条件

- AWS Bedrock 访问已启用，包含 Claude 模型权限
- GitHub 在 AWS 中配置为 OIDC 身份提供者
- IAM 角色具有 Bedrock 权限


### 必需的 Secrets


### Bedrock 工作流示例

```text
name: Claude PR Action
permissions:
  contents: write
  pull-requests: write
  issues: write
  id-token: write

on:
  issue_comment:
    types: [created]
  pull_request_review_comment:
    types: [created]

jobs:
  claude-pr:
    if: |
      (github.event_name == 'issue_comment' && contains(github.event.comment.body, '@claude')) ||
      (github.event_name == 'pull_request_review_comment' && contains(github.event.comment.body, '@claude'))
    runs-on: ubuntu-latest
    env:
      AWS_REGION: us-west-2
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Generate GitHub App token
        id: app-token
        uses: actions/create-github-app-token@v2
        with:
          app-id: ${{ secrets.APP_ID }}
          private-key: ${{ secrets.APP_PRIVATE_KEY }}

      - name: Configure AWS Credentials (OIDC)
        uses: aws-actions/configure-aws-credentials@v4
        with:
          role-to-assume: ${{ secrets.AWS_ROLE_TO_ASSUME }}
          aws-region: us-west-2

      - uses: anthropics/claude-code-action@v1
        with:
          github_token: ${{ steps.app-token.outputs.token }}
          use_bedrock: "true"
          claude_args: '--model us.anthropic.claude-sonnet-4-6 --max-turns 10'
```


## Google Vertex AI 集成


### 前置条件

- GCP 项目中启用 Vertex AI API
- 为 GitHub 配置 Workload Identity Federation
- 具有 Vertex AI 权限的服务账号


### 必需的 Secrets


### Vertex AI 工作流示例

```text
name: Claude PR Action
permissions:
  contents: write
  pull-requests: write
  issues: write
  id-token: write

on:
  issue_comment:
    types: [created]

jobs:
  claude-pr:
    if: github.event_name == 'issue_comment' && contains(github.event.comment.body, '@claude')
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Generate GitHub App token
        id: app-token
        uses: actions/create-github-app-token@v2
        with:
          app-id: ${{ secrets.APP_ID }}
          private-key: ${{ secrets.APP_PRIVATE_KEY }}

      - name: Authenticate to Google Cloud
        id: auth
        uses: google-github-actions/auth@v2
        with:
          workload_identity_provider: ${{ secrets.GCP_WORKLOAD_IDENTITY_PROVIDER }}
          service_account: ${{ secrets.GCP_SERVICE_ACCOUNT }}

      - uses: anthropics/claude-code-action@v1
        with:
          github_token: ${{ steps.app-token.outputs.token }}
          trigger_phrase: "@claude"
          use_vertex: "true"
          claude_args: '--model claude-sonnet-4-5@20250929 --max-turns 10'
        env:
          ANTHROPIC_VERTEX_PROJECT_ID: ${{ steps.auth.outputs.project_id }}
          CLOUD_ML_REGION: us-east5
```


## 从 Beta 版本升级（v1.0 重大变更）


### 升级前后对比

Beta 版本：

```text
- uses: anthropics/claude-code-action@beta
  with:
    mode: "tag"
    direct_prompt: "Review this PR for security issues"
    anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
    custom_instructions: "Follow our coding standards"
    max_turns: "10"
    model: "claude-sonnet-4-6"
```

GA 版本 (v1.0)：

```text
- uses: anthropics/claude-code-action@v1
  with:
    prompt: "Review this PR for security issues"
    anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
    claude_args: |
      --append-system-prompt "Follow our coding standards"
      --max-turns 10
      --model claude-sonnet-4-6
```


## 故障排除


### Claude 不响应 @claude 命令

- 确认 GitHub App 已正确安装
- 检查工作流是否已启用
- 确保 API 密钥已在仓库 Secrets 中设置
- 确认评论包含 @claude（不是 /claude）


## 后续章节

- CI 不运行在 Claude 的提交上
- 认证错误
- 安全注意事项
- 成本考虑
- 费用构成
- 成本优化建议
- 最佳实践
- 1、创建 CLAUDE.md
- 2、使用具体的 @claude 命令
- 3、配置适当的限制
- 4、CI/CD 自动化场景

## 复习重点

- 能说明 `Claude Code GitHub Actions` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
