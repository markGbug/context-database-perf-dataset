# Git：GitHub Actions

- 来源：[GitHub Actions](https://www.runoob.com/git/github-actions.html)
- 分类：DevOps / 工程化
- 技术：Git
- 笔记类型：练习笔记
- 章节序号：1796

## 本章内容

GitHub Actions 是 GitHub 内置的自动化平台，允许你在代码仓库中直接定义并运行自动化流程，无需借助任何外部 CI/CD 工具。

常见的用途包括：代码推送后自动运行测试、合并 PR 后自动部署到服务器、定时执行数据抓取脚本等。

GitHub Actions 对公开仓库完全免费，私有仓库每月有 2,000 分钟的免费额度。


## 核心概念

在开始编写配置文件之前，需要先理解以下几个核心概念，它们之间的关系如下：

```text
仓库（Repository）
└── Workflow（工作流）          ← 一个 .yml 文件 = 一个 Workflow
    ├── Event（触发事件）        ← 什么情况下启动这个 Workflow，如 push、PR
    └── Job（作业）× N          ← 一个 Workflow 可以包含多个并行或串行的 Job
        ├── Runner（运行器）     ← 执行 Job 的服务器，如 ubuntu-latest
        └── Step（步骤）× N     ← Job 内按顺序执行的一系列操作
            ├── Action          ← 可复用的封装好的操作，如 actions/checkout
            └── Run             ← 直接执行 Shell 命令
```


## 创建第一个 Workflow


### 1、目录结构

所有 Workflow 文件必须存放在仓库根目录的 .github/workflows/ 文件夹下，文件名以 .yml 或 .yaml 结尾，文件名可以自定义：

```text
your-repo/
├── .github/
│   └── workflows/
│       ├── ci.yml          ← 持续集成流程（如运行测试）
│       ├── deploy.yml      ← 部署流程
│       └── scheduled.yml   ← 定时任务
├── src/
├── package.json
└── README.md
```

一个仓库可以有多个 Workflow 文件，它们相互独立，分别由各自定义的事件触发。


### 2、最简单的 Workflow

下面是一个最基础的示例：每次向仓库推送代码时，打印一行"Hello, GitHub Actions！"：


## 实例

YAML 文件对缩进非常敏感，必须使用空格缩进，不能使用 Tab 键。建议使用 VS Code 并安装 YAML 插件，可以实时检测格式错误。


## 触发事件（on）

on 字段定义哪些事件会触发这个 Workflow。可以是单个事件，也可以是多个事件的组合。


### 1、常用触发事件


### 2、指定分支或路径过滤


## 实例


### 3、定时触发（schedule）

使用标准的 Cron 表达式定义执行时间，时区为 UTC（北京时间 = UTC+8，需换算）：


## 实例


### 4、手动触发（workflow_dispatch）

workflow_dispatch 允许在 GitHub 网页的 Actions 标签页中手动点击按钮启动 Workflow，还可以定义输入参数：


## 实例


## Jobs 与 Steps 详解


### 1、Job 的基本结构


## 实例


### 2、运行环境（runs-on）

GitHub 提供以下免费的托管运行器，可以按需选择：


### 3、Job 之间的依赖（needs）

默认情况下，多个 Job 并行运行。使用 needs 可以设置 Job 的执行顺序，形成串行依赖关系：


## 实例


### 4、条件执行（if）

通过 if 可以控制 Job 或 Step 是否执行，常用于区分分支、判断上一步是否成功等：


## 实例


## 环境变量与 Secrets


### 1、环境变量（env）

环境变量可以在 Workflow 的三个层级定义，作用范围依次缩小：


## 实例


## 后续章节

- 2、GitHub 内置变量（github 上下文）
- 实例
- 3、Secrets（敏感信息管理）
- 实例
- 常用 Actions 介绍
- 1、actions/checkout（拉取代码）
- 实例
- 2、actions/setup-node（配置 Node.js 环境）
- 实例
- 3、actions/setup-python（配置 Python 环境）
- 实例
- 4、actions/cache（缓存依赖加速构建）
- 实例
- 5、actions/upload-artifact / download-artifact（Job 间传递文件）
- 实例
- 矩阵构建（Matrix）

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `GitHub Actions` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
