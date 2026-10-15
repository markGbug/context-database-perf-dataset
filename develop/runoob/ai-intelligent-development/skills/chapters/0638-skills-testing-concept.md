# Skills（技能）：Skills 单元测试

- 来源：[Skills 单元测试](https://www.runoob.com/skills/skills-testing.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：概念卡
- 章节序号：0638

## 本章内容

写完 Skill 后，如何确认它真的按预期工作？靠手动测试既费时又容易遗漏。

本篇介绍如何为 Skill 建立系统性的测试用例，从脚本单元测试到端到端触发测试。


## Skill 测试的两个层次


## 层次一：脚本单元测试

脚本是 Skill 中最确定性的部分，适合用标准单元测试框架覆盖。


## 实例

运行测试：

```text
# 进入 Skill 目录后运行所有测试
cd my-skill/
pytest scripts/tests/ -v

# 生成覆盖率报告
pytest scripts/tests/ --cov=scripts --cov-report=term-missing
```

输出：

```text
scripts/tests/test_clean_data.py::test_remove_duplicates_basic  PASSED
scripts/tests/test_clean_data.py::test_remove_duplicates_empty  PASSED
scripts/tests/test_clean_data.py::test_fill_nulls_numeric       PASSED
scripts/tests/test_clean_data.py::test_strip_whitespace         PASSED
scripts/tests/test_clean_data.py::test_process_real_file        PASSED

5 passed in 0.12s
```


## 层次二：触发端到端测试

触发测试验证的是：当用户发出某个请求时，Claude 是否会使用这个 Skill。

测试用例以 JSON 格式定义，包含用户提示词和期望的行为断言。


## 实例

运行触发测试（需要 skill-creator 提供的 eval 工具）：


## 实例

测试用例的提示词要足够复杂，简单的"读取 CSV"类请求即使触发失败也不代表 Skill 有问题，因为 Claude 本身就能处理。好的测试用例应当是用户真实会提的多步骤、有明确输出要求的请求。


## 测试用例的覆盖范围


## 记忆卡片

- 一句话定义：`Skills 单元测试` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
