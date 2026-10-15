# Skills（技能）：自定义 Skills 生态系统搭建

- 来源：[Skills 生态系统搭建](https://www.runoob.com/skills/skills-ecosystem.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：概念卡
- 章节序号：0643

## 本章内容

当团队积累了多个 Skill 后，如何统一组织、管理和分发，是构建"私有 Skill 生态"的核心问题。


## 生态系统的三个层次


## 统一仓库结构

推荐将所有团队 Skill 放在同一个 Git 仓库中，用目录隔离不同 Skill。

```text
skills-repo/
├── README.md                  # 仓库总览，列出所有 Skill
├── .github/
│   └── workflows/
│       └── package.yml        # CI：自动打包 .skill 文件
├── skills/
│   ├── data-analyzer/         # Skill 1
│   │   ├── SKILL.md
│   │   └── scripts/
│   ├── doc-generator/         # Skill 2
│   │   ├── SKILL.md
│   │   └── scripts/
│   └── code-reviewer/         # Skill 3
│       ├── SKILL.md
│       └── scripts/
├── dist/                      # 打包好的 .skill 文件
│   ├── data-analyzer.skill
│   ├── doc-generator.skill
│   └── code-reviewer.skill
└── tools/
    └── build_all.sh           # 批量打包脚本
```


### 批量打包脚本


## 实例

```text
开始打包所有 Skill...
  正在打包：data-analyzer
  完成：dist/data-analyzer.skill
  正在打包：doc-generator
  完成：dist/doc-generator.skill
  正在打包：code-reviewer
  完成：dist/code-reviewer.skill

全部打包完成，共 3 个 Skill。
```


## GitHub Actions 自动化打包

每次向主分支提交代码时，自动打包所有 Skill 并发布为 Release 附件。


## 实例


## Skill 注册表（Registry）

当 Skill 数量增多后，用一个 JSON 注册表来管理所有 Skill 的元信息，方便检索和按需安装。


## 实例


## 团队 Skill 分发清单

为团队新成员准备一份 Skill 安装清单，让他们能快速配置好所有常用 Skill。

```text
# 团队 Skills 安装指南

## 必装 Skills（所有成员）

| Skill | 用途 | 下载地址 |
|-------|------|---------|
| data-analyzer | 数据分析与报表 | dist/data-analyzer.skill |
| doc-generator | 文档自动生成 | dist/doc-generator.skill |

## 按需安装

| Skill | 适合角色 | 下载地址 |
|-------|---------|---------|
| code-reviewer | 开发人员 | dist/code-reviewer.skill |

## 安装方式
1. 下载 .skill 文件
2. 在 Claude.ai 的 Settings → Skills 中上传文件
3. 安装完成后重新开始对话即可生效
```


## 记忆卡片

- 一句话定义：`Skills 生态系统搭建` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
