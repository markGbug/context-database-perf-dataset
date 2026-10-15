# Skills（技能）：Skill 代码审查

- 来源：[Skill 代码审查](https://www.runoob.com/skills/skills-project-code-review.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：练习笔记
- 章节序号：0650

## 本章内容

本项目构建一个代码审查 Skill，用户上传代码文件后，自动分析代码质量、风格问题和潜在 Bug。

目标：掌握工具链集成与结构化问题报告的生成。


## 项目需求分析


## 目录结构

```text
code-reviewer/
├── SKILL.md
└── scripts/
    ├── requirements.txt
    ├── check_python.py
    ├── check_js.py
    └── generate_report.py
```


## Python 代码检查脚本


## 实例

输出：

```text
{
  "status": "success",
  "file": "runoob_app.py",
  "grade": "B",
  "syntax_ok": true,
  "style_issues": [
    {"line": 12, "col": 1, "code": "E302", "message": "expected 2 blank lines"},
    {"line": 34, "col": 80, "code": "E501", "message": "line too long (103 > 100)"}
  ],
  "style_count": 5,
  "error_count": 3,
  "warning_count": 2,
  "complex_functions": []
}
```


## SKILL.md 完整内容

```text
---
name: code-reviewer
version: 1.0.0
description: >
  自动审查用户上传的代码文件，检查语法错误、风格问题和代码复杂度，
  生成带评级的问题报告并给出改进建议。当用户需要代码审查、
  检查代码质量、查找 Bug、评估代码规范时触发。
---

# 代码审查助手

## 执行流程

### 第一步：识别代码文件

获取用户上传的代码文件路径，识别编程语言（根据扩展名）：
- .py → Python 审查
- .js / .ts → JavaScript/TypeScript 审查
- 其他格式 → 告知暂不支持，列出支持的格式

### 第二步：运行自动化检查

Python 文件运行：
```bash
cd scripts/
python check_python.py <文件路径>
```

### 第三步：生成并解读报告

根据 JSON 输出，以人性化方式呈现结果：

1. **总体评级**：A（优秀）/ B（良好）/ C（需改进）/ F（语法错误）
2. **问题汇总表格**：行号、问题代码、描述
3. **Top 3 优先修复项**：选出最严重的 3 个问题，给出修复建议和示例

若文件无问题，给出简短正面评价：
> 代码检查通过！共扫描 X 行，未发现语法错误和明显风格问题。
```


## 测试用例


## 实例

运行审查：

```text
cd scripts/
python check_python.py tests/test_sample.py
```

输出：

```text
{
  "status": "success",
  "file": "test_sample.py",
  "grade": "B",
  "syntax_ok": true,
  "style_count": 5,
  "error_count": 4,
  "warning_count": 1,
  "complex_functions": []
}
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Skill 代码审查` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
