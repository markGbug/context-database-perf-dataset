# Codex：Codex AGENTS.md

- 来源：[Codex AGENTS.md](https://www.runoob.com/codex/codex-agents-md.html)
- 分类：AI / 智能开发
- 技术：Codex
- 笔记类型：学习笔记
- 章节序号：0205

## 本章内容

AGENTS.md 是 Codex 的自定义指令文件，允许你为 Codex 设置全局指导和工作流规范。

本节详细介绍如何创建和使用 AGENTS.md。


## 什么是 AGENTS.md？

Codex 在启动时会自动读取 AGENTS.md 文件，通过「全局配置 + 项目级覆写」的层级机制，让每次任务都能继承一致的工作约定，无论你打开的是哪个代码仓库。

AGENTS.md 是 Codex 在执行任何工作之前读取的指令文件，允许你：

- 设置全局编码规范
- 定义项目特定的工作流程
- 为不同目录提供不同的指导
- 标准化团队的开发实践

通过 AGENTS.md，你可以确保 Codex 在整个代码库中遵循一致的规范。


## Codex 如何发现指南

Codex 按以下优先级构建指令链。


### 三层加载机制

合并后的总大小上限默认为 32 KiB（由 project_doc_max_bytes 控制），超出部分会被截断。


## 第一步：创建全局配置

全局配置作用于所有项目，适合放通用工作约定。


### 创建配置目录

```text
mkdir -p ~/.codex
```

确保 Codex 主目录存在，所有全局配置都放在这个目录下。


### 编写全局约定

创建 ~/.codex/AGENTS.md 文件，写入所有项目通用的约定：

```text
# ~/.codex/AGENTS.md

## 全局工作约定

- 修改 JavaScript 文件后，始终运行 npm test
- 安装依赖时优先使用 pnpm
- 新增生产依赖前先请求确认
```


### 验证配置是否生效

运行以下命令，Codex 应当回显你写入的条目：

```text
codex --ask-for-approval never "Summarize the current instructions."
```

若需要临时全局覆写，可以创建 AGENTS.override.md，删除该文件即可恢复原始配置。


## 第二步：按仓库分层配置

项目级文件让 Codex 遵守仓库专属规范，同时仍会继承全局配置。


### 添加仓库级约定

在项目根目录创建 AGENTS.md：

```text
# AGENTS.md

## 仓库约定

- 提 PR 前运行 npm run lint
- 修改公共工具行为时，同步更新 docs/ 中的文档
```


### 为子目录添加覆写

对于有特殊需求的子目录（如 services/payments/），创建 AGENTS.override.md 进行局部覆写：

```text
# services/payments/AGENTS.override.md

## 支付服务规则

- 使用 make test-payments 替代 npm test
- 轮换 API Key 前必须通知安全频道
```


### 完整目录结构

以下是一个典型仓库加载 AGENTS.md 后的目录布局：

```text
repo/
├── AGENTS.md                          # 仓库级约定（加载）
└── services/
    ├── payments/
    │   ├── AGENTS.md                  # 被跳过（override 优先）
    │   └── AGENTS.override.md         # 支付服务覆写（加载）
    └── search/
        └── AGENTS.md                  # 搜索服务约定（加载）
```

同一目录下，AGENTS.override.md 存在时，同级的 AGENTS.md 会被跳过。


### 验证加载顺序

从子目录启动 Codex，查看加载的指令来源：

```text
codex --cd services/payments --ask-for-approval never \
  "List the instruction sources you loaded."
```

预期结果：依次列出全局文件、仓库根目录文件、支付服务覆写文件。


## 高级选项

以下两个功能适用于需要进一步定制指令加载行为的场景。


### 自定义文件名

如果项目已有约定俗成的 TEAM_GUIDE.md，可以在配置文件中追加到回退列表，Codex 会把它当作指令文件处理：

```text
# ~/.codex/config.toml
# 追加回退文件名并提高合并上限
project_doc_fallback_filenames = ["TEAM_GUIDE.md", ".agents.md"]
project_doc_max_bytes = 65536
```

修改后每个目录的检查顺序变为：AGENTS.override.md → AGENTS.md → TEAM_GUIDE.md → .agents.md，取第一个存在的文件。

修改配置后需重启 Codex 才能使 config.toml 的变更生效。


### 切换配置目录

通过 CODEX_HOME 环境变量，可以为不同项目或自动化流程使用独立的配置 profile：

```text
CODEX_HOME=$(pwd)/.codex codex exec "List active instruction sources"
```

此时 Codex 会从当前目录的 .codex 子目录读取全局配置，而非默认的 ~/.codex。


## 验证与调试

以下命令可以快速检查当前生效的指令来源。


### 快速检查

```text
# 从仓库根目录检查全局 + 项目指令
codex --ask-for-approval never "Summarize the current instructions."

# 从子目录检查嵌套覆写
codex --cd subdir --ask-for-approval never "Show which instruction files are active."
```


### 开启详细日志

若需要详细审计指令加载过程，可以开启 TUI 日志：

```text
# 输出 TUI 日志到本地目录
codex -c log_dir=./.codex-log
# 日志文件位于 ./.codex-log/codex-tui.log
```


## 常见问题排查

下表汇总了配置过程中可能遇到的问题及排查方向。


## 复习重点

- 能说明 `Codex AGENTS.md` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
