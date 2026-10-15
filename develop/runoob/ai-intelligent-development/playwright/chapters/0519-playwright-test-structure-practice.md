# Playwright：Playwright 测试结构与钩子

- 来源：[Playwright 测试结构与钩子](https://www.runoob.com/playwright/playwright-test-structure.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：练习笔记
- 章节序号：0519

## 本章内容

本章介绍 Playwright 测试的组织方式，包括测试分组、执行控制以及生命周期钩子的用法。


## test.describe() 测试分组

test.describe() 用于将相关的测试组织在一起，形成逻辑分组。


## 实例

测试报告会按照 describe 分组显示，方便查看结果。


## 嵌套 describe

test.describe() 可以嵌套，形成树状结构：


## 实例


## test.skip() 跳过测试

test.skip() 用于跳过某个测试，被跳过的测试不会执行。


## 实例


## test.fail() 标记预期失败

test.fail() 用于标记一个已知会失败的测试。


## 实例

test.fail() 的作用是反向标记：测试失败=符合预期，测试通过=异常（可能需要移除标记）。


## test.only() 只运行当前测试

test.only() 用于在开发调试时只运行特定测试，忽略文件中的其他测试。


## 实例

test.only() 是调试工具，不应提交到代码仓库。如果你在 playwright.config.ts 中设置了 forbidOnly: true，CI 上会检测到 only 并让构建失败。


## test.fixme() 标记待修复

test.fixme() 与 test.skip() 类似，但语义上表示"这个测试需要修复"。


## 实例


## test.slow() 标记慢测试

test.slow() 将测试的超时时间增加 3 倍。


## 实例


## 测试钩子（Hooks）

钩子函数让你在测试的不同阶段执行准备和清理工作。


### test.beforeEach() 与 test.afterEach()

beforeEach 在每个测试前执行，afterEach 在每个测试后执行。


## 实例


### test.beforeAll() 与 test.afterAll()

beforeAll 在当前作用域所有测试之前执行一次，afterAll 在所有测试之后执行一次。


## 实例

beforeAll 和 afterAll 不能访问 page fixture，因为 page 是每个测试独立的。如果需要操作页面，请使用 beforeEach。


## 钩子的作用域与执行顺序

钩子的作用域取决于它们所在的位置：


## 实例

执行顺序：外层钩子先执行，内层钩子后执行。

对于 A1 和 A2：先输出 "文件级 beforeEach"，再输出 "分组 A 的 beforeEach"。

对于 B1：只输出 "文件级 beforeEach"。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Playwright 测试结构与钩子` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
