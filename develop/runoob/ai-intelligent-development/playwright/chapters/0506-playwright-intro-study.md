# Playwright：Playwright 简介

- 来源：[Playwright 简介](https://www.runoob.com/playwright/playwright-intro.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：学习笔记
- 章节序号：0506

## 本章内容

Playwright 是由微软开发的一个开源 Web 自动化测试框架，用于在 Chromium、Firefox 和 WebKit 三大浏览器引擎中进行端到端测试。

简单来说，它就是一个可以帮你通过编程来控制浏览器的工具，我们可以把它想象成一个虚拟用户，它能像人一样在网页上进行各种操作，比如：点击按钮、填写表单、导航到不同的页面、截图和保存网页内容。

Playwright 是微软开源的现代浏览器自动化框架，用少量代码就能在 Chromium（Chrome/Edge）、Firefox、WebKit（Safari 引擎）里自动完成人类的浏览器操作：打开网页、点击、输入、拖拽、上传文件、截图/PDF、录制日志与回放，最常见的用途是 端到端（E2E）测试，也可做轻量爬取与流程自动化。

Playwright 提供 JS/TS、Python、Java、.NET 多语言 SDK，其中 JS/TS + Playwright Test 是最主流组合。


### 支持的浏览器

Playwright 使用的是官方浏览器的测试版本（Chromium 而非 Google Chrome，WebKit 而非 Safari），但行为与官方版本高度一致。


## Playwright 的主要应用场景

Playwright 不仅仅用于测试，它的强大功能使其在多个领域都大有作为：

- 端到端（E2E）测试： 这是 Playwright 最主要的应用。它可以模拟真实用户的使用场景，测试你的网站从头到尾的整个流程是否正常工作。
- Web 爬虫和数据抓取： 如果你想从网页上自动化地获取数据，Playwright 可以帮你轻松完成。它可以渲染 JavaScript 动态加载的内容，这比传统的爬虫工具更强大。
- 网页自动化： 任何重复性的网页操作，比如自动签到、批量下载文件、填写报告等，都可以用 Playwright 来自动化。
- 生成截图和 PDF： 你可以用 Playwright 来对网页进行截图，或者将网页内容保存为 PDF 文件。


## Playwright 能干什么？

用一句话总结：只要人能在浏览器里点的，Playwright 几乎都能自动化完成。

具体能力包括：

- 多浏览器支持：一次代码，能同时跑在 Chromium（Chrome/Edge）、Firefox、WebKit（Safari）上。
- 跨平台运行：支持 Windows、Linux、macOS。
- 跨语言调用：不仅支持 JavaScript/TypeScript，还支持 Python、C#、Java。
- 现代网页支持：对单页应用（SPA）、动态加载、iframe、多标签页都有稳定的处理。

举个例子： 你要测试一个"登录"功能。

- 手动测试：每次打开浏览器 → 输入账号密码 → 点击登录 → 检查页面。
- Playwright 测试：写一段脚本，自动完成上面的动作，还能重复执行上百次，毫不费劲。


## Playwright vs 其他测试工具


### Playwright vs Puppeteer

Puppeteer 适合简单的浏览器自动化脚本。

Playwright 在功能完备性和测试体验上全面超越，是测试场景的首选。


### Playwright vs Cypress

Cypress 的开发者体验优秀，调试界面友好。

如果你需要多浏览器支持、多标签页操作，或者大型测试套件的并行执行，Playwright 更适合。


### Playwright vs Selenium

提到浏览器自动化，很多人第一时间想到的是 Selenium。那 Playwright 和它相比，有啥不同？

一句话对比：

- Selenium 更像是"老牌全能选手"，历史悠久、生态庞大。
- Playwright 更像是"年轻小钢炮"，速度快，支持现代网页特性，API 也更友好。


## 适合哪些场景？

Playwright 不光能用来做测试，还能用在很多场景：

- 前端测试：自动测试网页的按钮、表单、导航等是否正常。
- 回归测试：新功能上线前，跑一遍全站测试用例，确保旧功能不出问题。
- 数据采集（爬虫）：抓取动态网页（比如需要滚动才能看到的数据）。
- 网页截图 & PDF：给页面生成截图或 PDF（比如生成报告）。
- 流程自动化：自动化重复操作（如自动登录、批量表单填写）。


## 为什么要学 Playwright？

- 初学者友好：安装简单，几行代码就能跑通。
- API 直观：用 page.click()、page.fill() 就能完成网页操作。
- 学了能赚钱：前端开发、测试工程师、甚至一些数据采集的兼职工作都会用到。
- 社区活跃：Playwright 的更新很快，文档清晰，遇到问题容易找到解决方案。

总结一句话： Playwright = 一个会自动帮你打开网页、点按钮、填表单、截屏的"智能机器人"，既能用来做测试，也能当爬虫，还能做自动化小工具。


## 为什么选择 Playwright？

对于初学者来说，Playwright 有几个非常吸引人的特点：

- 自动等待： 这是 Playwright 最强大的功能之一。在编写自动化脚本时，你经常需要等待某个元素加载或变得可见。Playwright 内置了智能的自动等待机制，它会自动等待元素变得可用，而无需你手动添加繁琐的 sleep 或 wait 函数。这让你的代码更简洁、更稳定。
- 快速且可靠： Playwright 的执行速度非常快，因为它直接与浏览器进行通信，而不是通过中间的协议。这种直接连接确保了操作的稳定性和可靠性。
- 强大的 API： Playwright 的 API 设计得非常人性化。它提供了丰富的操作方法，可以让你轻松地处理各种复杂的网页交互，比如处理弹窗、上传文件、管理新标签页等。
- 自带测试框架： Playwright 团队还提供了一个强大的测试运行器 @playwright/test。这个框架自带了断言库、测试报告生成器以及并行执行等高级功能，让编写和管理测试用例变得非常方便。

Playwright 最核心的优势在于它的跨浏览器支持。 它可以同时控制 Chromium（Google Chrome 和 Microsoft Edge）、Firefox 和 WebKit（Safari 的引擎）这三种主流浏览器。这意味着你只需要编写一套代码，就可以在所有这些浏览器上运行你的自动化脚本，大大减少了重复工作。


## Playwright 的四大核心特性


### 1. 真正的跨浏览器支持

Playwright 是唯一一个同时支持 Chromium、Firefox 和 WebKit 三大浏览器引擎的测试框架。

每个浏览器都有专门维护的驱动层（Chromium 使用 CDP，Firefox 使用 Juggler 协议，WebKit 使用 Playwright 自定义协议），确保底层操作的稳定性和一致性。


### 2. 自动等待机制

Playwright 在执行每个操作前，会自动等待元素变为可操作状态（附加到 DOM、可见、稳定、可接收事件、已启用）。

断言也会自动重试，直到条件满足或超时。

这从根本上解决了传统测试中最常见的 不稳定测试（flaky tests） 问题。


### 3. 测试隔离

Playwright 引入了 Browser Context 的概念，每个测试运行在独立的浏览器上下文（相当于一个全新的浏览器配置文件）中。

每个 context 拥有独立的 localStorage、sessionStorage、cookies，测试之间不会相互影响。

创建 context 的开销极低（毫秒级），远快于每次启动新的浏览器实例。


### 4. 多语言支持

Playwright 提供了 JavaScript/TypeScript、Python、Java、.NET 四种语言的 API，所有语言共享相同的设计理念和功能。

```text
npm init playwright@latest
```

```text
pip install playwright
```


## Playwright 产品矩阵

Playwright 不是一个单一的工具，而是一个包含多个组件的平台：

```text
npm init playwright@latest
```

```text
npm i playwright
```

```text
npx @playwright/mcp@latest
```

```text
npm i -g @playwright/cli@latest
```


## 复习重点

- 能说明 `Playwright 简介` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
