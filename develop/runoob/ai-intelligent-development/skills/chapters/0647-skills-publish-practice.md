# Skills（技能）：Skills 发布与团队共享

- 来源：[Skills 发布](https://www.runoob.com/skills/skills-publish.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：练习笔记
- 章节序号：0647

## 本章内容

开发完成的 Skill 需要经过打包、测试、文档化，才能分发给团队成员或公开发布。

本篇介绍从开发完成到上线发布的完整流程。


## 发布前的检查清单

发布前逐项确认，避免将未完成或有缺陷的 Skill 分发出去。


## 打包为 .skill 文件

发布前需将 Skill 目录打包为 .skill 文件，这是可分发的标准格式。


## 实例

```text
打包完成：dist/my-skill-v1.2.0.skill（共 8 个文件，42KB）
包含：
  SKILL.md
  scripts/process.py
  scripts/requirements.txt
  assets/template.xlsx
```


## 编写用户文档

在 SKILL.md 末尾或单独的 README.md 中，提供完整的用户说明。

```text
# 数据分析助手 v1.2.0

## 这个 Skill 能做什么

上传 CSV 或 Excel 文件后，自动完成以下工作：
- 统计各列的行数、均值、最大/最小值、空值比例
- 生成数据质量报告，标注需要清理的问题列
- 输出带统计图表的 Excel 报告文件

## 快速开始

1. 在对话中上传你的数据文件（.csv 或 .xlsx）
2. 说："帮我分析这份数据" 或 "生成统计报告"
3. 等待分析完成，下载生成的 Excel 报告

## 系统要求

- Python 3.8+
- pandas >= 2.0（首次运行时自动安装）

## 常见问题

**Q：文件太大怎么办？**
建议文件不超过 50MB。更大的文件请先筛选或抽样后上传。

**Q：支持哪些编码？**
支持 UTF-8 和 GBK。若文件乱码，请另存为 UTF-8 后重新上传。
```


## 分发渠道


### 通过 GitHub Releases 发布


## 实例


## 安装指引页面模板

如果你的 Skill 面向多人使用，可以为安装步骤专门写一份简明指引。

```text
## 安装方法

1. 前往 [Release 页面](https://github.com/yourname/skills/releases/latest)
2. 下载 `my-skill-v1.2.0.skill` 文件
3. 打开 Claude.ai → Settings（设置）→ Skills
4. 点击"上传 Skill"，选择下载的 .skill 文件
5. 安装完成后，开始新对话即可使用

安装后，在对话中发送以下内容可以验证安装成功：

> "我上传了一个 CSV 文件，请帮我做数据统计分析"

若 Skill 正常工作，Claude 会按照 Skill 的流程引导你完成分析。
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Skills 发布` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
