# Playwright：Playwright 运行测试

- 来源：[Playwright 运行测试](https://www.runoob.com/playwright/playwright-running-tests.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：学习笔记
- 章节序号：0528

## 本章内容

本章全面介绍 Playwright 测试的运行方式、命令行参数以及各种筛选技巧。


## 基本运行命令


## 实例


## 筛选特定测试


### 按文件路径

```text
# 运行单个测试文件
npx playwright test tests/login.spec.ts

# 运行目录中的所有测试
npx playwright test tests/user/

# 运行多个文件（空格分隔）
npx playwright test tests/login.spec.ts tests/register.spec.ts
```


### 按文件名关键词

```text
# 运行文件名中包含 "login" 或 "user" 的所有测试
npx playwright test login user
```


### 按测试名称筛选（-g / --grep）

```text
# 运行测试名称中包含 "登录" 的测试
npx playwright test -g "登录"

# 通过正则表达式筛选
npx playwright test -g "登录|注册"
```


### 按 Tag 筛选


## 实例

```text
# 只运行带 @smoke 标签的测试
npx playwright test --grep "@smoke"

# 跳过带 @slow 标签的测试
npx playwright test --grep-invert "@slow"
```


## 浏览器控制


### 指定浏览器（--project）

```text
# 只在 Chromium 上运行
npx playwright test --project=chromium

# 在多个浏览器上运行
npx playwright test --project=chromium --project=firefox
```


### 有头模式（--headed）

```text
# 显示浏览器窗口（默认无头）
npx playwright test --headed
```


### 指定浏览器可执行路径

```text
# 使用本地安装的 Chrome 而非 Playwright 的 Chromium
npx playwright test --project=chromium \
  --channel=chrome
```


## 执行模式


### UI 模式（--ui）

```text
# 在 UI 模式下运行（推荐开发和调试时使用）
npx playwright test --ui
```


### 调试模式（--debug）

```text
# 单步调试测试
npx playwright test --debug
```


## 并行与重复


### 控制并行数（--workers）

```text
# 使用 4 个 worker 并行运行
npx playwright test --workers=4

# 单线程运行（方便调试）
npx playwright test --workers=1
```


### 重复运行（--repeat-each）

```text
# 每个测试重复运行 3 次（检查稳定性）
npx playwright test --repeat-each=3
```


## 分片运行（--shard）

```text
# 在 CI 上分片运行（分 4 片，当前为第 1 片）
npx playwright test --shard=1/4

# 第 2 片
npx playwright test --shard=2/4
```

分片常用于 CI 中多台机器并行运行测试，每台机器只跑一部分，最终合并结果。


## 截图与 Trace 控制

```text
# 更新视觉回归的基准截图
npx playwright test --update-snapshots

# 强制生成 Trace 文件（即使配置中没有开启）
npx playwright test --trace on

# 查看最后一次运行的 Trace
npx playwright show-trace test-results/.../trace.zip
```


## 常用命令速查


## 复习重点

- 能说明 `Playwright 运行测试` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
