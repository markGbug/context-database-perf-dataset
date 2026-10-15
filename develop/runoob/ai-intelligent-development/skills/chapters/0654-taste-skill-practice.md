# Skills（技能）：Taste Skill

- 来源：[Taste Skill](https://www.runoob.com/skills/taste-skill.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：练习笔记
- 章节序号：0654

## 本章内容

Taste Skill 是一套给 AI 编程工具用的设计技能包，把布局变化、排版层次、动效规则等设计决策写成指令文件，让 AI 按规则做决策，而不是按训练数据的默认模式生成界面。


## AI 生成界面的"AI 味"是什么

用 Claude Code 或 Cursor 写前端，描述了半天想要的效果，生成出来的界面大概是这样的：大标题居中，副标题跟着，下面一个 CTA 按钮。

配色要么蓝白，要么深灰。卡片四等分，间距均匀，圆角适中。

整体看起来干净，但也说不出哪里不对 -- 就是感觉像模板。

换一个项目再生成，出来的东西和上次高度相似。再换，还是差不多。

不是代码有问题，跑起来完全没毛病。就是视觉上太"AI 味"了，一眼就能认出来是机器生成的。


## 为什么 AI 总是生成"AI 味"界面

AI 生成界面的方式是从训练数据里提取模式，写出来的东西自然倾向于出现频率最高的那种。

开发者教程、组件库示例、GitHub 上的开源项目 -- 这些数据里最多的是功能正确、布局中规中矩的界面。

AI 学到的是"怎么写出一个没有问题的界面"，而不是"怎么写出一个有设计感的界面"。

结果是：生成出来的东西功能完好，视觉上却普通。每个决定都是最保险的那个：居中布局风险最低，标准间距最省事，主流配色最不容易出错。

这个问题靠提示词很难根本上解决。你可以描述"现代感""高端感""设计感"，但这些词对 AI 来说太模糊，出来的结果通常还是那套东西加了点渐变。


## Taste Skill 的解决思路

Taste Skill 的做法很直接：把布局变化、排版层次、动效规则、间距逻辑这些具体的设计决策写成 AI 可以读懂的指令文件（SKILL.md）。

让 AI 在生成界面之前先加载这套规则，按照规则做决策，而不是按训练数据里最常见的模式来。

它相当于给 AI 配了一套设计偏好，让生成结果从"功能正确"往"视觉有意思"推一把。


## 安装

一条命令安装全部技能包。

```text
# 安装全部技能包
npx skills add https://github.com/Leonxlnx/taste-skill
```

只需要某一个技能包的话，加 --skill 参数指定。

```text
# 只安装默认主技能
npx skills add https://github.com/Leonxlnx/taste-skill --skill "design-taste-frontend"
```

安装完成后，AI 工具在生成界面时会自动加载对应的 SKILL.md 文件。不需要修改项目配置，也不需要写额外的提示词。


## 快速上手

装好之后，照常让 AI 生成界面，不需要改提示词。

```text
# 像平时一样描述需求即可
做一个 SaaS 产品的落地页，有导航、Hero 区域、功能介绍和定价表
```

这时 AI 会先读取 Taste Skill 的规则，再生成代码。

和没装之前生成出来的对比，布局的变化幅度、排版层次、动效处理方式都会有所不同。


## 技能包分类与选用

Taste Skill 拆成了几个独立的技能包，每个只做一件事，按需选用，不需要全部安装。


### 界面生成类

这类技能包直接影响 AI 生成界面时的设计决策，是最常用的。

默认主技能 design-taste-frontend 是 v2 版本，最通用。会自动读取你的需求，推断适合的设计语言，然后按三个维度生成代码。大部分项目从这个开始就够了。

```text
# 安装默认主技能（推荐先装这个试试）
npx skills add https://github.com/Leonxlnx/taste-skill --skill "design-taste-frontend"
```


### 流程辅助类

这类技能包解决的是 AI 工作流程中的问题，不直接控制视觉风格。

```text
# 安装改造现有项目的技能包
npx skills add https://github.com/Leonxlnx/taste-skill --skill "redesign-existing-projects"
```

装好之后告诉 AI "按照 skill 审计一下当前的界面，找出问题再修改"，它会先分析再动手，不会乱改。


### 图片生成类

这三个技能包用于生成设计参考图，不输出代码，配合 ChatGPT Images 等工具使用，生成后再交给编程 AI 实现。


## 三个可调参数

默认主技能 design-taste-frontend 里有三个数值参数，范围 1-10，可以直接编辑 SKILL.md 文件调整。

```text
# 编辑 SKILL.md 调整参数（找到以下三行修改数值即可）
DESIGN_VARIANCE    7    # 布局变化幅度，1-10，想更现代就调高
MOTION_INTENSITY   5    # 动效深度，1-10，落地页可以推到 8
VISUAL_DENSITY     3    # 信息密度，1-10，内容展示页保持低值
```

改完保存，AI 下次生成时会按新的参数来。


## 使用前需要了解的几点


### v2 还在迭代中

默认主技能目前是 v2 实验版，官方说明是"actively iterating toward v2.0.0 stable"，行为偶尔会有变化。

如果需要稳定可预期的结果，用 v1。

```text
# 安装 v1 稳定版
npx skills add https://github.com/Leonxlnx/taste-skill --skill "design-taste-frontend-v1"
```


### 它影响的是设计决策，不是代码质量

Taste Skill 改变的是 AI 在布局、排版、动效上的倾向，不处理功能逻辑或代码结构的问题。

如果生成的代码有 bug，这不是它能解决的。


### 效果依赖 AI 工具对 SKILL.md 的理解

不同的 AI 工具对技能文件的遵循程度有差异。

Claude Code 和 Cursor 通常执行得比较忠实，ChatGPT 可以直接把 SKILL.md 贴进对话里使用。


### 框架无关

规则针对的是设计意图，不绑定特定框架，React、Vue、Svelte 都可以用。


## 快速上手建议

如果你用 Claude Code 或 Cursor 做前端，可以先装默认主技能试一下。

```text
# 第一步：安装默认主技能
npx skills add https://github.com/Leonxlnx/taste-skill --skill "design-taste-frontend"
```

然后让 AI 生成一个你之前做过的页面，和原来的结果对比一下，看看差别在哪里。

如果有改造现有项目的需求，试试 redesign-existing-projects，让 AI 先分析再动手，比直接说"帮我改好看点"要可控很多。

项目地址：https://github.com/Leonxlnx/taste-skill


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Taste Skill` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
