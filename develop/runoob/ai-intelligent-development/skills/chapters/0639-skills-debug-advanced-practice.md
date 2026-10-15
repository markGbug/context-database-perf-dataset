# Skills（技能）：Skills 日志与调试进阶

- 来源：[Skills 日志与调试进阶](https://www.runoob.com/skills/skills-debug-advanced.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：练习笔记
- 章节序号：0639

## 本章内容

入门调试靠 print，进阶调试靠系统性的日志机制。

本篇介绍如何为 Skill 脚本建立结构化日志，以及在复杂执行流程中定位问题的进阶技巧。


## 用 logging 替代 print

print 适合快速调试，但在正式 Skill 中应改用 Python 标准库的 logging 模块。

logging 的优势是可以控制输出级别——开发时输出 DEBUG 信息，生产时只输出 WARNING 以上。


## 实例

```text
[10:23:01] [DEBUG]   __main__ - 调试信息：文件路径 = /mnt/user-data/uploads/runoob.csv
[10:23:01] [INFO]    __main__ - 开始处理文件
[10:23:01] [WARNING] __main__ - 文件大小超过 50MB，处理可能较慢
[10:23:01] [ERROR]   __main__ - 文件读取失败：FileNotFoundError
```


## 执行时间追踪

当 Skill 执行较慢时，需要找出耗时的瓶颈步骤。


## 实例

```text
[10:23:05] [INFO] load_csv 耗时 0.342 秒
[10:23:05] [INFO] calculate_stats 耗时 0.018 秒
[10:23:05] [INFO] 读取并清洗数据 耗时 0.361 秒
```


## 结构化日志：输出 JSON 格式

当日志需要被程序解析（而非人工阅读）时，JSON 格式更合适。


## 实例

```text
{"timestamp": "2026-05-18T10:23:05", "level": "info",    "event": "file_loaded",   "file": "/mnt/user-data/uploads/runoob.csv", "rows": 1024}
{"timestamp": "2026-05-18T10:23:05", "level": "warning", "event": "null_detected", "column": "score", "count": 12}
{"timestamp": "2026-05-18T10:23:05", "level": "error",   "event": "parse_failed",  "reason": "编码不是 UTF-8"}
```


## 调试 SKILL.md 的指令执行

当 Claude 没有按照 SKILL.md 的指令执行时，可以通过在 SKILL.md 中插入"检查点"来定位问题。

```text
## 调试检查点（开发模式，发布前删除）

在执行每个步骤前，先以以下格式输出一行状态确认：

`[STEP N] 开始：{步骤名称}，输入：{关键参数}`

示例：
`[STEP 1] 开始：读取文件，输入：/mnt/user-data/uploads/runoob.csv`
`[STEP 2] 开始：数据清洗，输入：1024 行`

这样可以在出错时快速定位到哪个步骤失败。
```

调试检查点是临时的。调试完成后，务必从 SKILL.md 中删除这些指令，否则正式使用时用户会看到多余的调试输出。


## 常见调试场景速查


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Skills 日志与调试进阶` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
