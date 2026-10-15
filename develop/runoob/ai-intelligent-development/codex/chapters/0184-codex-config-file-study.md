# Codex：Codex 配置与定制

- 来源：[Codex 配置与定制](https://www.runoob.com/codex/codex-config-file.html)
- 分类：AI / 智能开发
- 技术：Codex
- 笔记类型：学习笔记
- 章节序号：0184

## 本章内容

Codex 提供丰富的配置选项，让你定制 Agent 的行为以适应不同的工作需求。

默认情况下 Codex App 会根据你的系统设置语言，如果没有可以通过 Settings（ 设置 ）：

选择 General（常规） 常规选项修改你需要的语言：

同样如果要中文改英文，勾选英文即可：


## Codex App 的设置

打开方式：点击应用菜单中的设置（ Settings ），或按 Cmd + ,：

设置界面如下所示：

常规（General）：配置文件的打开方式、命令输出在对话线程中的显示量。还可设置多行提示需要 Cmd+Enter 确认，以及防止任务运行期间系统休眠。

通知（Notifications）：设置任务完成通知的触发时机，以及是否由应用主动请求系统通知权限。

Agent 配置（Agent Configuration）：App 中的 Codex Agent 与 IDE 和 CLI 扩展共享同一套配置。常用选项可在 App 内直接调整，高级选项需编辑 config.toml 文件（后文说明）。

外观（Appearance）：支持选择基础主题，调整强调色、背景色和前景色，以及更换 UI 字体和代码字体。可将自定义主题分享给他人。

Codex 宠物（Codex Pets）:可选的动态陪伴角色，路径：Settings（设置） > Appearance（外观） > Pets（宠物），可选择内置宠物或从本地 Codex 主目录加载自定义宠物。

操作方式：

- 在输入框中输入 /pet
- 使用 Settings > Appearance 中的 Wake Pet 或 Tuck Away Pet
- 按 Cmd+K / Ctrl+K 后运行同名命令

宠物悬浮窗可在使用其他应用时持续显示当前 Codex 工作状态（运行中 / 等待输入 / 待审查），并附有简短进度提示。

自定义宠物（创建流程）：

```text
$skill-installer hatch-pet
```

安装后在命令菜单中选择 Force Reload Skills，再执行：

```text
$hatch-pet create a new pet inspired by my recent projects
```

Git: 统一分支命名规范，配置是否启用强制推送（force push），并设置 Codex 自动生成提交信息（commit message）和 PR 描述时所用的提示语。

环境：可以查看项目目录及添加项目。

工作树： 利用 Git worktree 让 Codex 在同一项目中并行处理多个任务。

浏览器使用（Browser Use）：安装或启用内置 Browser 插件，管理网站白名单和黑名单。默认情况下，Codex 使用任何网站前都会先询问用户；将网站从黑名单移除后，Codex 将恢复询问行为。详见应用内浏览器文档。

电脑操控（Computer Use）：仅限 macOS。可查看桌面应用访问权限及相关偏好设置。如需撤销系统级权限，请前往 macOS 隐私与安全性 中修改屏幕录制或辅助功能权限。

已归档的项目（Archived Threads）：列出所有已归档的对话，显示日期和项目上下文。点击取消归档（ Unarchive） 可恢复指定线程。


## 配置文件位置

Codex 配置文件分层管理：


### 配置合并规则

配置按优先级合并：

- 托管配置优先级最高
- 项目配置覆盖用户配置
- 用户配置作为默认值


## 基础配置项


## 基础配置


## AGENTS.md

AGENTS.md 是项目级的 Agent 指令文件，定义 Codex 在该项目中的行为规范。


### 文件发现顺序

- 读取全局 ~/.codex/AGENTS.md
- 从项目根目录向下搜索每个目录
- 更近目录的规则覆盖更远的


### AGENTS.md 示例


## 项目 AGENTS.md


### 子目录覆盖

可以在子目录放置 AGENTS.override.md：


## 子目录规则

AGENTS.md 大小限制为 32 KiB，超过会被截断。


## Skills（技能）

Skills 是可复用的自定义能力，封装常用任务逻辑。


### 技能目录位置


### 技能结构

```text
skill-name/
├── SKILL.md       # 技能定义（必需）
├── scripts/       # 可选脚本
├── references/    # 可选参考文档
└── assets/        # 可选资源
```


### 创建技能


## 技能定义


### 技能触发


## Subagents（子代理）

Subagents 允许将复杂任务拆分给多个 Agent 并行处理。


### 内置代理类型


### 配置子代理


## 子代理配置


### 自定义代理


## 自定义代理


## Rules（规则）

Rules 定义命令执行策略，控制哪些命令可以自动执行。


## 后续章节

- 规则文件
- 规则定义
- 决策类型
- Hooks（钩子）
- 启用 Hooks
- 启用 Hooks
- Hook 事件
- 配置 Hook
- Hook 配置
- 常见问题
- Q: 配置修改后如何生效？
- Q: AGENTS.md 应放在哪里？
- Q: Skills 和 Rules 的区别？
- Q: 如何查看当前配置？

## 复习重点

- 能说明 `Codex 配置与定制` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
