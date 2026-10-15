# ASP：ASP Browser Capabilities 组件

- 来源：[ASP BrowserCap](https://www.runoob.com/asp/asp-browser.html)
- 分类：后端开发
- 技术：ASP
- 笔记类型：练习笔记
- 章节序号：0740

## 本章内容

## ASP Browser Capabilities 组件

ASP Browser Capabilities 组件会创建一个 BrowserType 对象，这个对象可测定访客浏览器的类型、性能和版本号。

当浏览器连接到服务器时，就会向服务器发送一个 HTTP User Agent 报头。这个报头包含关于浏览器的信息。

BrowserType 对象会把报头中的信息与服务器上名为 "Browscap.ini" 的文件中的信息作比较。

如果报头中的浏览器类型和版本号与 "Browsercap.ini" 文件中信息匹配，那么我们就可以使用 BrowserType 对象列出这个匹配的浏览器的相关属性。如果上述情况不匹配，这个对象会把每个属性设置为 "UNKNOWN"。


### 语法


## ASP Browser Capabilities 实例

下面的实例会在 ASP 文件中创建一个 BrowserType 对象，并显示当前浏览器性能的一些信息：


## 实例

输出：


## Browscap.ini 文件

"Browscap.ini" 文件用于声明属性，并设置各浏览器的默认值。

这部分内容不是关于如何维护 Browscap.ini 文件的教程，我们只提供一些关于 "Browsercap.ini" 的基础知识和概念，让您对该文件有个大概的了解。

"Browscap.ini" 文件可包含下面的信息：

- ActiveXControls - 支持 ActiveX® 控件？
- Backgroundsounds - 支持背景声音？
- Cdf - 支持针对网络广播的频道定义格式？
- Tables - 支持表格？
- Cookies - 支持 cookies？
- Frames - 支持框架？
- Javaapplets - 支持 Java applets？
- Javascript - 支持 JScript？
- Vbscript - 支持 VBScript？
- Browser - 规定浏览器的名称
- Beta - 浏览器是否为 beta 软件？
- Platform - 规定浏览器运行的平台
- Version - 规定浏览器的版本号

"Browscap.ini" 文件可能如下所示：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ASP BrowserCap` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
