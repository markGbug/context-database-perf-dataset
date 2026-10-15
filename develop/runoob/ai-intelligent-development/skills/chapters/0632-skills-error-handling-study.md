# Skills（技能）：Skills 错误处理与容错

- 来源：[Skills 错误处理与容错](https://www.runoob.com/skills/skills-error-handling.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：学习笔记
- 章节序号：0632

## 本章内容

一个只能在理想情况下运行的 Skill 是脆弱的。

健壮的 Skill 需要预见常见错误，给出清晰的反馈，并尽可能自动恢复。


## 错误处理的三个层次


## 在 SKILL.md 中定义错误处理策略

SKILL.md 中应当包含一个明确的错误处理章节，告诉 Claude 遇到问题时该怎么做。


## 实例


## 脚本中的标准错误处理模式

Python 脚本应使用 try-except 结构，并统一返回包含 status 字段的 JSON。


## 实例

```text
# 文件存在时的成功输出：
{
  "status": "success",
  "data": {
    "file": "/mnt/user-data/uploads/runoob.txt",
    "lines": 128,
    "chars": 5432
  }
}

# 文件不存在时的错误输出：
{
  "status": "input_error",
  "code": "FILE_NOT_FOUND",
  "message": "文件不存在：/mnt/user-data/uploads/missing.txt",
  "hint": "请检查文件路径是否正确，文件是否存在且非空"
}
```


## 依赖自动安装的容错模式

当脚本依赖的 Python 包未安装时，可以在脚本中自动尝试安装。


## 实例

自动安装只适用于开发和轻量级场景。在生产环境的 Skill 中，应将依赖写入文档，由用户预先安装，而不是在运行时自动安装。


## 错误信息的书写规范

好的错误信息能帮助用户快速定位问题，差的错误信息只会让人困惑。


## 实例


## 复习重点

- 能说明 `Skills 错误处理与容错` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
