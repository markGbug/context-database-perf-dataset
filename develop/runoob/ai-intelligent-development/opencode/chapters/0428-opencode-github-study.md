# OpenCode：OpenCode GitHub

- 来源：[OpenCode GitHub](https://www.runoob.com/opencode/opencode-github.html)
- 分类：AI / 智能开发
- 技术：OpenCode
- 笔记类型：学习笔记
- 章节序号：0428

## 本章内容

OpenCode 可以深度集成 GitHub 工作流，让 AI 直接参与 Issue、Pull Request 和代码审查流程。

通过在评论中输入 /opencode 或 /oc，即可触发 AI 自动执行任务。

OpenCode GitHub = 把 AI 变成你的自动化开发成员，直接参与 Issue、PR 和代码流程。


## 一、核心能力

- Issue 分析：自动理解问题并给出解释
- 自动修复：创建分支并提交 PR
- 代码审查：分析 PR 并提出改进建议
- 自动化执行：基于 GitHub Actions 运行

特点：

- 运行在你自己的 GitHub Runner 中
- 安全可控，不依赖外部服务器执行代码


## 二、快速安装（推荐）

在 GitHub 项目根目录运行：

```text
opencode github install
```

该命令会自动完成：

- 安装 GitHub App
- 创建 GitHub Actions 工作流
- 引导配置 API Key


## 三、手动安装（进阶）


### 1、安装 GitHub App

访问：

```text
https://github.com/apps/opencode-agent
```

安装到你的仓库


### 2、添加工作流文件

创建文件：

```text
.github/workflows/opencode.yml
```

示例：

```text
name: opencode

on:
  issue_comment:
    types: [created]
  pull_request_review_comment:
    types: [created]

jobs:
  opencode:
    if: |
      contains(github.event.comment.body, '/oc') ||
      contains(github.event.comment.body, '/opencode')
    runs-on: ubuntu-latest
    permissions:
      id-token: write
    steps:
      - name: Checkout repository
        uses: actions/checkout@v6
        with:
          fetch-depth: 1
          persist-credentials: false

      - name: Run OpenCode
        uses: anomalyco/opencode/github@latest
        env:
          ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
        with:
          model: anthropic/claude-sonnet-4-20250514
```


### 3、配置 Secrets

在 GitHub 仓库中：

- 进入 Settings → Secrets → Actions
- 添加 API Key（如 ANTHROPIC_API_KEY）


## 四、配置参数说明

说明：

- 默认使用 OpenCode GitHub App 的 Token
- 也可以使用 GITHUB_TOKEN 或 PAT


## 五、支持的触发事件


## 六、常见使用方式


### 1、解释 Issue

在 Issue 评论：

```text
/opencode explain this issue
```

AI 会总结问题并解释


### 2、自动修复 Issue

```text
/opencode fix this
```

自动：

- 创建分支
- 修改代码
- 提交 Pull Request


### 3、修改 PR

```text
Delete the attachment from S3 when the note is removed /oc
```

直接在 PR 上执行修改


### 4、代码行级操作（非常强）

在 PR 的 Files 页面评论：

```text
/oc add error handling here
```

OpenCode 会自动获取：

- 文件路径
- 行号
- 上下文 diff

无需手动说明位置


## 七、定时任务（自动化）

示例：每周扫描 TODO

```text
on:
  schedule:
    - cron: "0 9 * * 1"
```

示例 prompt：

```text
Review the codebase for TODO comments and summarize them
```

注意：

- 定时任务必须提供 prompt
- 需要写权限（contents / pull-requests）


## 八、PR 自动审查

示例：

```text
on:
  pull_request:
    types: [opened, synchronize]
```

默认行为：

- 分析代码质量
- 检测潜在 Bug
- 提出改进建议


## 九、Issue 自动分类

可以自动处理新 Issue，例如：

- 过滤垃圾账号
- 自动回复建议
- 补充文档说明

注意：

- issues 事件必须提供 prompt


## 十、自定义提示词（高级用法）

可以覆盖默认行为：

```text
prompt: |
  Review this pull request:
  - Check for bugs
  - Suggest improvements
```

用于：

- 统一代码规范
- 定制审查标准
- 自动化团队流程


## 十一、安全与权限

推荐权限配置：

```text
permissions:
  id-token: write
  contents: write
  pull-requests: write
  issues: write
```

说明：

- 最小权限原则
- 仅开放必要能力


## 复习重点

- 能说明 `OpenCode GitHub` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
