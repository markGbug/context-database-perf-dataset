# Playwright：Playwright 并行、分片与重试

- 来源：[Playwright 并行](https://www.runoob.com/playwright/playwright-parallel-sharding.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：概念卡
- 章节序号：0540

## 本章内容

本章介绍 Playwright 的并行执行策略、分片运行和失败重试机制，帮助你高效运行大规模测试套件。


## 并行执行

Playwright 默认使用多个 Worker 进程并行运行测试，充分利用多核 CPU。


### fullyParallel 配置

fullyParallel 控制同一文件内的测试是否并行执行。


## 实例

当 fullyParallel: false 时，同一文件内的测试串行执行，不同文件之间并行执行。

当 fullyParallel: true 时，所有测试完全并行（包括同一文件内的）。


### workers 数量控制


## 实例


### 串行测试

使用 test.describe.serial 强制同一组内的测试串行执行。


## 实例

尽量避免使用串行测试，因为它破坏了测试隔离性。

如果测试需要按顺序执行，考虑将多个步骤合并到一个测试中。


### 局部并行控制

通过 test.describe.configure 可以控制单个分组的并行模式。


## 实例


## Sharding 分片运行

分片（Sharding）将测试分散到多台 CI 机器上执行，缩短总体运行时间。


### 使用方式

```text
# 机器 1：运行第 1/4 片
npx playwright test --shard=1/4

# 机器 2：运行第 2/4 片
npx playwright test --shard=2/4

# 机器 3：运行第 3/4 片
npx playwright test --shard=3/4

# 机器 4：运行第 4/4 片
npx playwright test --shard=4/4
```


### 合并分片报告

所有机器运行完毕后，合并生成的报告文件。

```text
# 每台机器生成报告（不自动打开）
npx playwright test --shard=1/4 --reporter=blob

# 合并所有 blob 报告
npx playwright merge-reports --reporter=html ./all-blob-reports
```


### GitHub Actions 中的分片配置


## 实例


## 重试机制

重试（Retries）让失败的测试自动再次运行，缓解偶发的不稳定因素。


### 配置重试


## 实例


### 单个文件或分组设置重试


## 实例


### 重试策略


## 记忆卡片

- 一句话定义：`Playwright 并行` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
