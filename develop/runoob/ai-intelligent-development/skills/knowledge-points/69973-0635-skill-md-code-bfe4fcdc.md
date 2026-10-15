# 知识点 69973：Skills（技能）：Skills 与工具链集成 - 在 SKILL.md 中声明工具依赖

- 来源：[Skills 与工具链集成](https://www.runoob.com/skills/skills-toolchain.html)
- 来源章节：[0635-skills-toolchain-practice.md](../chapters/0635-skills-toolchain-practice.md)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 所在小节：在 SKILL.md 中声明工具依赖
- 知识类型：代码
- 原章节序号：0635

## 原文片段

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

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `在 SKILL.md 中声明工具依赖` 这一小节和 `Skills 与工具链集成` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
