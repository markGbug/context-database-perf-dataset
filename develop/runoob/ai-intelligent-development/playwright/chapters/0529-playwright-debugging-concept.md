# Playwright：Playwright 调试工具

- 来源：[Playwright 调试工具](https://www.runoob.com/playwright/playwright-debugging.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：概念卡
- 章节序号：0529

## 本章内容

本章介绍 Playwright 的三大调试工具：UI Mode、Trace Viewer 和命令行 Debug 模式。


## UI Mode 完整介绍

UI Mode 是 Playwright 内置的图形化测试界面，提供探索、运行和调试测试的一站式体验。


### 启动 UI Mode

```text
npx playwright test --ui
```


### 测试列表浏览

启动后，左侧边栏显示所有测试文件。

你可以展开每个文件和 describe 块，单独运行、查看、Watch 或调试每个测试。


### Watch Mode

点击 Watch 按钮后，Playwright 会监听文件变化，一旦测试代码或源代码更新，自动重新运行受影响的测试。


### 时间轴视图（Timeline）

在测试执行后，顶部会显示时间轴视图，用不同颜色标记导航和操作。

你可以悬停查看每个步骤的快照，双击选中一个时间段，查看该时间段的详细日志。


### DOM Snapshot

在时间轴中点击某个步骤，右侧会显示该时刻的 DOM 快照。

你可以看到页面在操作前后的实际状态，快速定位问题。


### 测试过滤

UI Mode 支持多种过滤方式：

- 按测试名称搜索
- 按 @tag 过滤
- 按项目（Project）过滤
- 按状态过滤：通过（passed）、失败（failed）、跳过（skipped）


## Trace Viewer 深度调试

Trace Viewer 是 Playwright 的记录回放工具，能让你像调试录制一样检查测试的每一步。


### 配置 Trace 收集


## 实例


### 打开 Trace

```text
# 本地打开
npx playwright show-trace path/to/trace.zip
```

也可以上传到 trace.playwright.dev 在线查看。


### Trace 包含的信息


### 使用 Trace 定位失败

在 Trace Viewer 的时间线中找到失败步骤，查看该步骤前后页面的 DOM 状态和网络请求，定位失败原因。

Trace 是最强大的调试工具。当测试在 CI 上失败但你无法本地重现时，下载 CI 生成的 Trace 文件可以离线分析失败原因。


## --debug 模式与 page.pause()


### --debug 命令行模式

```text
npx playwright test --debug
```

功能：

- 自动打开 Playwright Inspector 窗口
- 逐个操作单步执行
- 在浏览器 DevTools 中调试
- 使用 F10（Step Over）和 F11（Step Into）控制执行


### page.pause() 暂停执行


## 实例

使用 page.pause() 后运行测试，Playwright 会自动打开 Inspector 窗口，让你逐步骤检查页面状态。


## 三种调试方式的选择


## 记忆卡片

- 一句话定义：`Playwright 调试工具` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
