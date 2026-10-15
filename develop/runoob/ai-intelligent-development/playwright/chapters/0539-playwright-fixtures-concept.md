# Playwright：Playwright Fixtures 与参数化

- 来源：[Playwright Fixtures](https://www.runoob.com/playwright/playwright-fixtures.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：概念卡
- 章节序号：0539

## 本章内容

本章介绍 Playwright 的 Fixture 机制、如何创建自定义 Fixture 以及参数化测试的技巧。


## 什么是 Fixture

Fixture（夹具）是 Playwright 测试函数参数的依赖注入机制。

每个测试通过解构参数的方式获取所需的 Fixture（如 { page }），Playwright 负责创建和清理。


## 实例


## 内置 Fixture 速查


## 自定义 Fixture

通过 test.extend() 创建自定义 Fixture，可以注入额外的依赖或覆盖内置 Fixture。


## 实例


### 使用自定义 Fixture


## 实例


## Fixture 的作用域

Fixture 有三种作用域，通过 scope 选项控制。


## 实例

Worker 级 Fixture 在同一 Worker 进程内的多个测试间共享，适合数据库连接等创建开销大的资源。


## 覆盖内置 Fixture

你可以覆盖内置 Fixture 来改变默认行为。


## 实例


## Fixture 自动清理

Fixture 的清理逻辑在 use() 调用之后执行，类似于 afterEach 的效果。


## 实例


## 参数化测试

Playwright 没有内置的参数化机制，但可以通过循环动态生成测试。


## 实例


## 测试注解（Annotations）

注解用于给测试添加元数据，在报告器中可以查看和过滤。


## 实例


## 记忆卡片

- 一句话定义：`Playwright Fixtures` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
