# Skills（技能）：使用现有 Skills

- 来源：[使用现有 Skills](https://www.runoob.com/skills/use-existing-skills.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：学习笔记
- 章节序号：0623

## 本章内容

现在市场上其实已经有了很多大家编写好的 Skills。

比如 Anthropic 官方提供的 Claude Skills： https://github.com/anthropics/skills 。

该仓库是 Anthropic 官方 Claude 技能合集，配套 Agent Skills 开放标准，支持动态加载拓展 AI 专项能力，技能覆盖设计、开发、企业办公、全品类文档编辑，多数开源，文档底层能力仅供源码参考。

我们可以将本仓库注册为 Claude Code 的插件市场，只需在 Claude Code 中执行以下命令：

```text
/plugin marketplace add anthropics/skills
```

然后就可以使用 /plugin 查看：

安装指定技能集的步骤：

- 浏览并安装插件（Browse and install plugins）
- 选择 anthropic-agent-skills 插件源
- 选择 document-skills（文档技能） 或 example-skills（示例技能）
- 点击立即安装（Install now）

我们也可直接通过命令安装上述两类插件：

```text
/plugin install document-skills@anthropic-agent-skills
/plugin install example-skills@anthropic-agent-skills
```

注意：使用插件安装的 skills 目录在 ～/claude/plugins/marketplaces/ 下。

插件安装完成后，需要重启一下 Claude Code。

使用的时候只需在指令中提及技能名称即可调用，例如安装 document-skills 插件后，可向 Claude Code 下达指令：

```text
使用 PDF 技能提取 path/to/some-file.pdf 文件中的表单字段
```

或者创建一个 PPT：


## Agent Skills 相关资源整理


## 复习重点

- 能说明 `使用现有 Skills` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
