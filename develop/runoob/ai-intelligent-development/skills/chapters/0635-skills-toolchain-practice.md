# Skills（技能）：Skills 与工具链集成

- 来源：[Skills 与工具链集成](https://www.runoob.com/skills/skills-toolchain.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：练习笔记
- 章节序号：0635

## 本章内容

Skills 可以通过与外部工具链集成，Skill 可以完成单靠 Claude 无法完成的任务。

本篇介绍如何在 Skill 中调用命令行工具、系统工具及第三方库，并提供一个完整的集成示例。


## Skills 可以调用的工具类型

调用外部工具前，先确认工具在运行环境中已安装。Claude 沙箱中预装了常用工具（python3、pip、node、npm），但 pandoc、ffmpeg 等需要额外安装。


## 在脚本中调用外部命令

Python 的 subprocess 模块是调用外部命令的标准方式，推荐统一封装成工具函数复用。


## 实例


## 检查工具是否可用

在 Skill 执行前检查所需工具是否安装，能在任务中途失败前给出清晰提示。


## 实例

```text
检查工具依赖...
  已安装：pandoc → /usr/bin/pandoc
  未安装：ffmpeg  安装命令：sudo apt-get install ffmpeg
  未安装：convert  安装命令：sudo apt-get install imagemagick

请先安装缺少的工具。
```


## 在 SKILL.md 中声明工具依赖

用 YAML frontmatter 的 compatibility 字段列出所有外部依赖，让用户安装 Skill 前就知道需要准备什么。

```text
---
name: doc-converter
description: >
  将文档在不同格式间转换，支持 Markdown、HTML、PDF、Word。
  当用户需要格式转换、导出文档时触发。
compatibility:
  tools:
    - pandoc >= 2.14   # 文档格式转换
    - python >= 3.8    # 运行辅助脚本
  python_packages:
    - pypdf >= 3.0     # PDF 处理
    - python-docx >= 1.0
---
```


## 集成 Node.js 工具

通过 npx 可以直接调用 npm 包中的 CLI 工具，无需全局安装。


## 实例

npx --yes 首次运行时会自动下载工具包，需要网络连接到 npm registry。在网络受限的环境中应提前全局安装：npm install -g prettier。


## 工具调用结果的标准化处理

不同工具的输出格式各不相同，建议在 Skill 层统一封装，对外只暴露一致的结构。


## 完整集成示例：Markdown 转 PDF 报告

以下示例将 pandoc 与 Python 脚本结合，实现一个完整的 Markdown → PDF 生成 Skill 脚本。


## 实例

```text
正在转换：/mnt/user-data/uploads/runoob_report.md
{
  "status": "success",
  "output": "/mnt/user-data/outputs/runoob_report_20260518_102305.pdf",
  "size_kb": 248
}
```

在 SKILL.md 中调用该脚本：

```text
## 执行转换

获取用户上传的 .md 文件路径后，运行：

```bash
python scripts/md_to_pdf.py <文件路径>
```

解析 JSON 输出：
- status 为 "success"：调用 present_files 展示 output 路径的文件
- status 为 "error"：将 message 内容展示给用户，说明可能原因
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Skills 与工具链集成` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
