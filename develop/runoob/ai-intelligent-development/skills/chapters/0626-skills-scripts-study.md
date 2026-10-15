# Skills（技能）：Skills 脚本扩展

- 来源：[Skills 脚本扩展](https://www.runoob.com/skills/skills-scripts.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：学习笔记
- 章节序号：0626

## 本章内容

除了在 SKILL.md 中编写指令外，你还可以通过 scripts 目录为技能添加可执行代码。

本节将教你如何使用脚本来扩展技能的功能。


## 为什么使用脚本

使用脚本可以：

- 封装复杂的逻辑，避免在 SKILL.md 中写大量代码
- 提供经过测试的可靠实现
- 让代理可以重复使用相同的工具和函数
- 处理更复杂的输入输出操作

提示：当你在多次执行中发现代理重复实现相同逻辑时，这往往是创建脚本的好时机。


## 脚本目录结构

脚本应该放在技能目录的 scripts/ 子目录下：


## 目录结构


## 脚本编写规范


### 1. 自包含性

脚本应该尽量自包含，或者清楚地记录依赖关系。


## 自包含脚本示例


### 2. 清晰的错误处理

脚本应该提供有用的错误信息，帮助代理理解出了什么问题。


## 错误处理示例


### 3. 处理边界情况

脚本应该优雅地处理各种边界情况，而不是崩溃。


## 边界情况处理示例


## 在 SKILL.md 中引用脚本

当技能需要执行脚本时，在 SKILL.md 中说明如何调用它。

引用脚本:

```text
## PDF 文本提取

使用脚本提取 PDF 中的文本：

```bash
python scripts/extract_pdf.py input.pdf
```

脚本会从 input.pdf 提取所有文本并输出到标准输出。

如果需要将结果保存到文件：

```bash
python scripts/extract_pdf.py input.pdf > output.txt
```
```

注意：引用脚本时使用相对于技能根目录的路径。


## 支持的脚本语言

支持的脚本语言取决于你使用的代理实现。常见的选项包括：

提示：在选择脚本语言时，考虑目标用户的运行环境。如果不确定，Python 是最安全的选择。


## 完整示例：PDF 处理技能

让我们看一个完整的示例，展示如何结合 SKILL.md 和脚本：


## 技能结构

SKILL.md 内容:

```text
---
name: pdf-tool
description: 处理 PDF 文件，包括提取文本、填写表单、合并文件。使用场景：处理 PDF、提取文本、填写表单、合并 PDF。
---

## 提取 PDF 文本

从 PDF 文件中提取文本内容：

```bash
python scripts/extract.py input.pdf
```

输出是提取的纯文本内容。

## 填写 PDF 表单

使用 JSON 数据填写 PDF 表单：

```bash
python scripts/fill_form.py input.pdf data.json output.pdf
```

data.json 格式：
```json
{
  "field_name": "字段值",
  "another_field": "另一个值"
}
```

## 合并 PDF

将多个 PDF 文件合并为一个：

```bash
python scripts/merge.py output.pdf input1.pdf input2.pdf input3.pdf
```

## 依赖安装

需要安装 pdfplumber 和 PyPDF2：

```bash
pip install pdfplumber PyPDF2
```
```


## 两种使用方式

在 Skill 中使用代码有两种方式：


## 一次性命令

当现有的包管理器工具已经能满足需求时，直接在 SKILL.md 的指令中引用即可，无需创建 scripts/ 目录。

以下是各语言生态的常用运行方式：


### uvx（Python）

uvx 是 uv 自带的工具运行命令，会在隔离环境中运行 Python 包，且缓存积极，重复运行几乎瞬间完成。


## 实例


### pipx（Python）

pipx 是 uvx 的成熟替代方案，可通过系统包管理器安装（如 brew install pipx）。


## 实例


### npx（Node.js）

npx 随 npm 自带，按需下载并运行 npm 包。


## 实例


### go run（Go）

Go 自带的工具运行命令，直接编译并运行远程包。


## 实例

编写一次性命令的建议：固定版本号（如 npx eslint@9.0.0）以确保行为一致；在 SKILL.md 中声明前置条件（如"需要 Node.js 18+"）；当命令变得复杂时，应将其提取到 scripts/ 目录。


## 后续章节

- 在 SKILL.md 中引用脚本
- 实例
- 实例
- 自包含脚本
- Python 自包含脚本（PEP 723）
- 实例：Python 自包含脚本
- 实例
- Deno 自包含脚本
- 实例：Deno 自包含脚本
- 实例
- Bun 自包含脚本
- 实例：Bun 自包含脚本
- 实例
- Ruby 自包含脚本
- 实例：Ruby 自包含脚本
- 实例

## 复习重点

- 能说明 `Skills 脚本扩展` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
