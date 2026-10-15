# Playwright：Playwright 测试

- 来源：[Playwright 测试](https://www.runoob.com/playwright/playwright-first-test.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：练习笔记
- 章节序号：0511

## 本章内容

本章带领你编写并运行第一个 Playwright 测试，理解测试的基本组成和执行流程。


## 运行示例测试

初始化项目后，先运行一下自动生成的示例测试，确认一切正常：

```text
# 运行所有测试
npx playwright test
```

运行后你会看到类似以下的输出：

```text
Running 6 tests using 4 workers

  ✓  1 [chromium] › tests/example.spec.ts:3:1 › has title (2.1s)
  ✓  2 [chromium] › tests/example.spec.ts:10:1 › get started link (1.8s)
  ✓  3 [firefox] › tests/example.spec.ts:3:1 › has title (1.9s)
  ✓  4 [firefox] › tests/example.spec.ts:10:1 › get started link (1.7s)
  ✓  5 [webkit] › tests/example.spec.ts:3:1 › has title (2.3s)
  ✓  6 [webkit] › tests/example.spec.ts:10:1 › get started link (2.0s)

  6 passed (12s)
```

从输出中可以看到：测试在 3 个浏览器上各运行了 2 个测试，共 6 个测试全部通过。


## 创建第一个测试文件

清空 tests/example.spec.ts 的内容，我们来从头写一个测试。


## 实例

运行这个测试：

```text
npx playwright test tests/first-test.spec.ts
```

预期输出：

```text
Running 1 test using 1 worker

  ✓  1 [chromium] › tests/first-test.spec.ts:4:1 › 访问 RUNOOB 首页并检查标题 (2.5s)

  1 passed (2.5s)
```


## test() 函数详解

test() 是 Playwright Test 的核心函数，用于定义一个测试用例。


### 基本语法


## 实例


### 参数说明


## page fixture 是什么

{ page } 是测试函数参数中的解构赋值，它从 Playwright 提供的 fixtures 对象中提取 page。

page 是一个 Page 对象，代表了一个浏览器标签页。

每个测试都拥有自己独立的 page 实例：

最常用的是 page，绝大多数操作都通过它完成。


## page.goto() 导航

page.goto(url) 是 Playwright 中最基础的操作之一，用来导航到指定 URL。


## 实例

waitUntil 选项有三个可选值：

在绝大多数情况下使用默认的 'load' 即可，Playwright 的自动等待机制会处理后续的元素可用性问题，无需使用 'networkidle'。


## expect() 断言

expect() 是 Playwright 的断言方法，用来验证测试结果是否符合预期。


## 实例

Playwright 的断言有一个关键特性：自动重试。

如果断言条件暂时不满足，Playwright 会不断重试，直到条件满足或超时。

这意味着你不需要写 waitFor 或 sleep 来等待页面就绪。


## 测试的 async/await 模式

Playwright 的所有操作都是异步的，因此测试函数必须声明为 async。

所有浏览器操作（goto、click、fill 等）和断言（expect）都必须使用 await 关键字。


## 实例

如果忘记写 await，测试可能会在不正确的时机断言，导致测试不稳定或意外通过。务必在每次调用 Playwright API 时加上 await。


## 理解测试输出

我们再看一个稍带断言失败的测试，以理解测试输出：


## 实例

运行后，输出大致如下：

```text
Running 1 test using 1 worker

  ✘  1 [chromium] › tests/fail-demo.spec.ts:4:1 › 一个故意失败的测试 (5.2s)

  1 failed
    tests/fail-demo.spec.ts:4:1 › 一个故意失败的测试
```

同时会自动打开 HTML 报告，显示详细的失败信息和错误截图。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Playwright 测试` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
