# Skills（技能）：Skills 监控与可观测性

- 来源：[Skills 监控与可观测性](https://www.runoob.com/skills/skills-monitoring.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：学习笔记
- 章节序号：0648

## 本章内容

Skill 发布后，如何知道它工作得好不好？是否频繁出错？哪些步骤最慢？

本篇介绍如何为 Skill 建立可观测性，通过日志和指标了解运行状态。


## 可观测性的三个维度


## 结构化日志的输出规范

Skill 脚本应将运行日志写入固定路径的文件，便于事后查阅。


## 实例

```text
{"ts": "2026-05-18T10:23:05+00:00", "level": "info",  "event": "skill_start",    "skill": "data-analyzer", "file": "/mnt/user-data/uploads/runoob.csv"}
{"ts": "2026-05-18T10:23:05+00:00", "level": "info",  "event": "step_complete",  "skill": "data-analyzer", "step": "clean", "rows_removed": 3, "elapsed_ms": 240}
{"ts": "2026-05-18T10:23:07+00:00", "level": "info",  "event": "skill_complete", "skill": "data-analyzer", "output": "/mnt/user-data/outputs/report.xlsx", "elapsed_ms": 1830}
{"ts": "2026-05-18T10:23:07+00:00", "level": "error", "event": "step_failed",    "skill": "data-analyzer", "step": "generate_chart", "error": "openpyxl not found"}
```


## 指标聚合：统计执行次数与成功率

从日志文件中提取关键指标，了解 Skill 的整体运行状况。


## 实例

```text
{
  "total_runs":     42,
  "total_errors":   3,
  "success_rate":   "92.9%",
  "avg_elapsed_ms": 1650,
  "recent_errors": [
    {"ts": "2026-05-18T09:12:00+00:00", "event": "step_failed", "step": "generate_chart", "error": "openpyxl not found"}
  ]
}
```


## 执行追踪：记录每步耗时

当某次执行特别慢时，通过步骤级别的耗时记录可以快速定位瓶颈。


## 实例

```text
{
  "skill": "data-analyzer",
  "total_ms": 1203,
  "steps": [
    {"name": "读取文件",  "elapsed_ms": 312},
    {"name": "数据清洗",  "elapsed_ms": 108},
    {"name": "生成报告",  "elapsed_ms": 783}
  ]
}
```

可观测性不是只有大规模系统才需要的。即使是个人使用的 Skill，在出现问题时，一份清晰的日志文件往往能将排查时间从几小时缩短到几分钟。


## 复习重点

- 能说明 `Skills 监控与可观测性` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
