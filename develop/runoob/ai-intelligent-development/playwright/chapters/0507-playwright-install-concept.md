# Playwright：Playwright 安装

- 来源：[Playwright 安装](https://www.runoob.com/playwright/playwright-install.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：概念卡
- 章节序号：0507

## 本章内容

Playwright 是一个 Node.js 库，所以需要我们本地安装 Node.js，如果你已经安装了可以跳过。


### 1、安装 Node.js

Playwright 官方推荐使用 Node.js。

- 打开 Node.js 官网
- 下载并安装 LTS（长期支持版）
- 验证是否安装成功： node -v npm -v 能看到版本号即可。

更多安装可以参考：https://www.runoob.com/nodejs/nodejs-install-setup.html


### 2、新建项目目录

如果成功安装 node，我们就可以开始 Playwright 的安装与使用。

在命令行执行：

```text
mkdir runoob-playwright-demo
cd runoob-playwright-demo
```


### 3、初始化并安装 Playwright

执行：

```text
npm init playwright@latest
```

安装过程会提示：

- 选择语言：JavaScript 或 TypeScript，熟悉哪个选哪个
- 是否要安装测试示例：推荐选 Yes（方便学习）
- 是否下载浏览器：选 Yes（Playwright 会下载 Chromium、Firefox、WebKit 三大引擎）

安装完成后，你的项目目录大概长这样：

```text
playwright-demo/
├─ tests/                # 示例测试用例
├─ playwright.config.js  # 配置文件
├─ package.json
└─ node_modules/
```


### 4、使用 yarn 初始化

```text
yarn create playwright
```


### 5、使用 pnpm 初始化

```text
pnpm create playwright
```

三种包管理器的初始化效果完全相同，选择你熟悉的一个即可。


## 手动安装

如果你已有项目，想手动添加 Playwright，可以分两步完成。


### 第一步：安装 npm 包

```text
# 安装 Playwright Test 作为开发依赖
npm i -D @playwright/test

# 如果只需要浏览器自动化库（不用测试运行器）
npm i playwright
```


### 第二步：安装浏览器

```text
# 安装所有浏览器（Chromium、Firefox、WebKit）
npx playwright install

# 或者只安装特定浏览器
npx playwright install chromium
npx playwright install firefox
npx playwright install webkit
```

浏览器二进制文件默认下载到操作系统缓存目录（如 macOS 的 ~/Library/Caches/ms-playwright/），不会占用你的项目空间。


## 安装的浏览器说明

Playwright 安装的是浏览器的测试版本，而非你日常使用的浏览器：

这些测试版本与用户日常使用的浏览器存在微小差异，但在绝大多数测试场景中表现一致。


## 验证安装

安装完成后，运行以下命令验证是否成功：

```text
# 查看已安装的 Playwright 版本和浏览器
npx playwright --version
```

预期输出大致如下：

```text
Version 1.52.0
```

运行示例测试来验证一切正常：

```text
npx playwright test
```

如果看到测试运行的输出（包括通过和失败的测试），说明安装成功。


## 常见安装问题


### 下载浏览器很慢

浏览器二进制文件较大（约 400-500 MB），下载速度取决于网络环境。

可以通过设置环境变量使用国内镜像：

```text
# 设置下载源为国内镜像
export PLAYWRIGHT_DOWNLOAD_HOST=https://npmmirror.com/mirrors/playwright/
npx playwright install
```


### Linux 系统缺少系统依赖

在 Linux 上运行 Playwright 需要安装额外的系统库。

```text
# 安装 Playwright 所需的系统依赖
npx playwright install-deps

# 如果只需要某个浏览器对应的依赖
npx playwright install-deps chromium
```

在 Docker 容器中使用 Playwright 时，请使用微软官方 Docker 镜像（mcr.microsoft.com/playwright），它已预装所有依赖。


## 第一个脚本：Hello World

新建一个 test.js 文件，写入以下内容：


## 实例

运行：

```text
node test.js
```

以上是一个 Playwright 的简单实例，可以截图百度的首页。


## 记忆卡片

- 一句话定义：`Playwright 安装` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
