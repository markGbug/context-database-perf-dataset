# Pi Agent：Pi Agent 提示词模板

- 来源：[Pi Agent 提示词模板](https://www.runoob.com/pi-agent/pi-agent-prompt-templates.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：练习笔记
- 章节序号：0489

## 本章内容

提示词模板是预定义的 Markdown 片段，通过简短命令即可展开为完整提示词，提高重复性工作的效率。


## 模板概述

提示词模板的工作方式很简单：

- 创建一个 Markdown 文件，定义模板内容
- 在编辑器中输入 /模板名 来调用
- 模板会自动展开并填入编辑器

模板支持参数替换，让同一个模板可以用于不同的具体场景。


## 创建模板

模板是带有 YAML Frontmatter 的 Markdown 文件。

文件名（不含 .md）即为模板的命令名。

创建一个代码审查模板：


## 实例

保存到 ~/.pi/agent/prompts/review.md 后，在编辑器中输入 /review 即可展开使用。


## 模板位置

Pi Agent 会在固定的几个位置查找模板，作用范围各不相同。

模板发现是非递归的，prompts/ 子目录中的模板不会被自动加载。

如果模板放在子目录，需要在 settings.json 的 prompts 数组中显式添加该路径。


## 参数系统

模板支持丰富的参数系统，让同一个模板适应不同场景：

$ARGUMENTS 会把全部参数原样拼接，适合只需要一整段文本的模板：


## 实例

保存为 ~/.pi/agent/prompts/translate.md 后，用 /translate 把这段话翻译成英文 调用。


### 带参数模板示例

下面的模板组合使用位置参数和尾部参数，适合"类型 + 名称 + 补充说明"这类输入。


## 实例

$1 取第一个参数作为框架，$2 取第二个参数作为组件名。

${@:3} 表示从第三个参数开始的所有内容，用于承载零散的功能描述。

使用方式：

```text
/component React Button "onClick 事件处理" "disabled 状态支持" "loading 加载状态"
```

展开后的效果：

```text
使用 React 创建一个 Button 组件，功能包括：onClick 事件处理 disabled 状态支持 loading 加载状态
```


### 默认值示例

参数缺失时用默认值兜底，模板在不带参数调用时也能正常工作。


## 实例

保存到 ~/.pi/agent/prompts/summarize.md 后，用 /summarize 调用。

使用 /summarize 时默认输出 5 个要点。

使用 /summarize 10 时输出 10 个要点。

两种调用的展开结果对比如下：

```text
/summarize
→ 用 5 个要点总结当前项目的主要变更和状态。

/summarize 10
→ 用 10 个要点总结当前项目的主要变更和状态。
```


## argument-hint 参数提示

在 Frontmatter 中设置 argument-hint 可以帮助用户了解模板需要的参数：


## 实例

在自动补全下拉菜单中，这个模板会显示为：

```html
→ pr   <PR-URL>  — 从 URL 审查 PR，分析代码和问题
```

保存到 ~/.pi/agent/prompts/pr-review.md 后，用 /pr-review https://github.com/runoob/repo/pull/12 调用。

使用 <尖括号> 表示必填参数，[方括号] 表示可选参数。


## 实用模板示例

下面三个模板覆盖了日常开发中最常见的三类请求，可直接复制后按需调整。


### Git 提交信息生成

以下模板按 Conventional Commits 规范生成提交信息。


## 实例

保存到 ~/.pi/agent/prompts/commit.md 后，暂存变更再用 /commit 调用。


### 代码重构请求

以下模板把重构目标拆成明确的检查项，避免 AI 只改格式不动结构。


## 实例

保存到 ~/.pi/agent/prompts/refactor.md 后，用 /refactor src/utils/date.ts 调用。


### Bug 修复请求

以下模板强制 AI 按固定步骤排查，减少"上来就改代码"的情况。


## 实例

保存到 ~/.pi/agent/prompts/fix-bug.md 后，用 /fix-bug 登录后列表不刷新 调用。


## 模板加载规则

模板的发现与加载遵循以下规则，排查"模板没出现"时先看这里。

输入 /模板名 后如果没有出现在补全列表里，先确认文件是否位于 prompts/ 根目录。

放在 .pi/prompts/ 的项目模板还需要先通过项目信任检查，否则同样不会被加载。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pi Agent 提示词模板` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
