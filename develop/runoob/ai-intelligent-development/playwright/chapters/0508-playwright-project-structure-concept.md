# Playwright：Playwright 项目结构

- 来源：[Playwright 项目结构](https://www.runoob.com/playwright/playwright-project-structure.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：概念卡
- 章节序号：0508

## 本章内容

成功初始化 Playwright 项目后，你的项目目录中会生成一系列文件和文件夹，本章详细解读每个部分的用途。


## 初始化的项目结构一览

运行 npm init playwright@latest 后，项目目录中会生成以下结构：

```text
your-project/
├── playwright.config.ts      # Playwright 配置文件
├── package.json              # 项目依赖与脚本
├── package-lock.json         # 依赖锁定文件
├── tests/                    # 测试文件目录
│   └── example.spec.ts       # 示例测试文件
├── tests-examples/           # 更多示例测试（可选）
│   └── demo-todo-app.spec.ts
├── .github/                  # GitHub Actions 配置（可选）
│   └── workflows/
│       └── playwright.yml
└── node_modules/             # npm 依赖包
```


## playwright.config.ts —— 配置文件

这是 Playwright 的核心配置文件，控制测试运行的所有方面。


## 实例

playwright.config.ts 是控制 Playwright 行为的核心入口，第 15 篇会对每个配置项做详细说明。


## package.json —— 依赖与脚本

初始化后，package.json 中会新增 Playwright 相关的内容：


## 实例

你也可以添加更多自定义脚本：


## 实例


## tests/ 目录 —— 测试文件

tests/ 目录是默认的测试文件存放位置（由 testDir 配置指定）。

初始化的示例测试文件内容如下：


## 实例

测试文件命名建议：使用 .spec.ts（TypeScript）或 .spec.js（JavaScript）后缀。


## tests-examples/ 目录 —— 更多示例

如果你在初始化时选择了包含示例测试，tests-examples/ 目录中会有一个更完整的测试示例：

demo-todo-app.spec.ts 演示了真实 Todo 应用的完整测试场景，包括添加任务、完成状态切换、过滤功能等。

这是一个很好的学习参考，你可以运行来看看效果：

```text
npx playwright test tests-examples/
```


## .github/workflows/ —— CI 配置

如果你在初始化时选择了添加 GitHub Actions，.github/workflows/playwright.yml 文件会被自动生成。

这个工作流会在每次推送代码或创建 PR 时自动运行 Playwright 测试。


## 浏览器存放位置

Playwright 安装的浏览器二进制文件不在项目目录中，而是存放在操作系统缓存目录：

```text
~/Library/Caches/ms-playwright/
```

```text
%USERPROFILE%\AppData\Local\ms-playwright\
```

```text
~/.cache/ms-playwright/
```

你也可以设置自定义存放路径：

```text
# 设置浏览器安装路径
export PLAYWRIGHT_BROWSERS_PATH=/your/custom/path
npx playwright install
```


## node_modules/ —— 依赖包

Playwright 的核心依赖 @playwright/test 安装在 node_modules/ 中。

依赖内部包含了 Playwright 的完整运行时，包括与浏览器通信的协议层。

除了通过 npm 安装的 Node.js 包外，Playwright 还依赖浏览器二进制文件（存放在系统缓存中），两者缺一不可。


## 记忆卡片

- 一句话定义：`Playwright 项目结构` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
