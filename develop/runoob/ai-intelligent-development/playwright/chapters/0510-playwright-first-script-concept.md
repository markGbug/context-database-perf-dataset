# Playwright：Playwright 第一个脚本

- 来源：[Playwright 第一个脚本](https://www.runoob.com/playwright/playwright-first-script.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：概念卡
- 章节序号：0510

## 本章内容

在编写代码之前，理解 Playwright 的核心概念至关重要，最核心的三个对象是 Browser、BrowserContext 和 Page，这三个对象构成了你与网页交互的基础：

- Browser（浏览器）：这是自动化过程的起点。一个 Browser 实例代表了一个实际的浏览器，例如 Chromium、Firefox 或 WebKit。你可以启动一个浏览器，然后在其内部创建多个独立的会话。
- BrowserContext（浏览器上下文）：一个 BrowserContext 就像一个独立的浏览器会话。它完全隔离了页面、本地存储、cookies 等数据。这使得你可以在一个浏览器中同时运行多个互不影响的自动化任务，就像你在隐身模式下打开了多个标签页一样。
- Page（页面）：Page 是你进行实际操作的地方。它代表了浏览器上下文中的一个标签页或窗口。所有的操作，如点击、输入、导航、截图等，都是在 Page 对象上执行的。

三者之间的关系：

一个 Browser 可以包含多个 BrowserContext，而一个 BrowserContext 可以包含多个 Page。通常，我们只需要一个 Browser 和一个 BrowserContext，但在某些需要隔离数据的场景下，BrowserContext 就显得非常有用。


## 编写你的第一个脚本

接下来我们将编写一个简单的脚本，它会启动浏览器，访问百度，然后截取一张图片。

创建一个名为 baidu_script.js 的文件，并粘贴以下代码：


## 实例

代码详解：

- const { chromium } = require('playwright');：从 Playwright 库中导入 chromium 模块。你可以根据需要替换为 firefox 或 webkit。
- await chromium.launch({ headless: false });：启动一个 Chromium 浏览器实例。headless: false 是一个关键选项，它会显示浏览器窗口，让你能看到脚本的执行过程。
- await browser.newContext(); 和 await context.newPage();：这三行代码组合起来，就是打开了一个新的浏览器标签页。
- await page.goto('https://www.baidu.com');：导航到指定的 URL。这是最常用的方法之一。
- await page.screenshot({ path: 'baidu_homepage.png' });：截取当前页面的截图，并将其保存到文件中。
- await browser.close();：关闭浏览器，释放系统资源。


### 脚本运行

打开终端或命令提示符，进入你的项目目录，然后执行以下命令：

```text
node baidu_script.js
```

执行后，你会看到一个浏览器窗口自动打开，加载百度首页，然后窗口关闭。在你的项目文件夹中，会生成一个名为 baidu_homepage.png 的截图文件。


### 调试模式

在编写更复杂的脚本时，你可能需要调试。

Playwright 提供了一个强大的调试工具，我们只需在运行脚本时，在命令行前添加 PWDEBUG=1：

```text
PWDEBUG=1 node baidu_script.js
```

运行后，你会看到一个 Playwright 调试窗口，可以逐步执行代码，检查页面元素，并实时看到脚本的每一步操作，这对于定位问题非常有帮助。


### 查看运行结果

除了命令行输出和截图文件，你还可以通过以下方式检查脚本的运行结果：

- console.log()：在脚本中加入 console.log() 语句，可以打印变量的值或确认某个步骤是否执行。
- 截图：利用 page.screenshot() 功能，在关键步骤保存截图，可以直观地看到页面的状态。
- 文件操作：你可以将抓取到的数据写入本地文件，以便后续分析。


## 记忆卡片

- 一句话定义：`Playwright 第一个脚本` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
