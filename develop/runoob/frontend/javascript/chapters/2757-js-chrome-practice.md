# JavaScript：Chrome 浏览器中执行 JavaScript

- 来源：[JavaScript Chrome 中运行](https://www.runoob.com/js/js-chrome.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：练习笔记
- 章节序号：2757

## 本章内容

本章节为大家介绍如何在 Chrome 浏览器上进行 JavaScript 代码的运行与调试。

Chrome 是由 Google 开发的免费网页浏览器，对于前端开发来说（尤其是调试代码）非常方便。

Chrome 官网地址：https://www.google.com/intl/zh-CN/chrome/。

我们在 Chrome 浏览器中可以通过按下 F12 按钮或者右击页面，选择"检查"来开启开发者工具。

也可以在右上角菜单栏选择 "更多工具"=》"开发者工具" 来开启：


## 1、Console 窗口调试 JavaScript 代码

打开开发者工具后，我们可以在 Console 窗口调试 JavaScript代码，如下图：

上图中我们在 > 符号后输入我们要执行的代码 console.log("runoob")，按回车后执行。

我们也可以在其他地方复制一段代码过来执行，比如复制以下代码到 Console 窗口，按回车执行：

```javascript
console.log("runoob-1")
console.log("runoob-2")
```

清空 Console 窗口到内容可以按以下按钮：


## 2、Chrome snippets 小脚本

我们也可以在 Chrome 浏览器中创建一个脚本来执行，在开发者工具中点击 Sources 面板，选择 Snippets 选项卡，在导航器中右击鼠标，然后选择 Create new snippet 来新建一个脚本文件：

如果你没看到 Snippets ，可以点下面板上到 >> 就能看到了。

点击 Create new snippet 后，会自动创建一个文件，你只需在右侧窗口输入以下代码，然后按 Command+S（Mac）或 Ctrl+S（Windows 和 Linux）保存更改即可。

```javascript
console.log("runoob-1")
console.log("runoob-2")
```

保存后，右击文件名，选择 "Run" 执行代码：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `JavaScript Chrome 中运行` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
