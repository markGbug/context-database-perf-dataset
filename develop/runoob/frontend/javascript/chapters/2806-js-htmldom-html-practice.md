# JavaScript：JavaScript HTML DOM - 改变 HTML

- 来源：[DOM HTML](https://www.runoob.com/js/js-htmldom-html.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：练习笔记
- 章节序号：2806

## 本章内容

HTML DOM 允许 JavaScript 改变 HTML 元素的内容。


## 改变 HTML 输出流

JavaScript 能够创建动态的 HTML 内容：

今天的日期是： document.write(Date());

在 JavaScript 中，document.write() 可用于直接向 HTML 输出流写内容。


## 实例


## 改变 HTML 内容

修改 HTML 内容的最简单的方法是使用 innerHTML 属性。

如需改变 HTML 元素的内容，请使用这个语法：

本例改变了 <p>元素的内容：


## 实例

本例改变了 <h1> 元素的内容：


## 实例

实例讲解：

- 上面的 HTML 文档含有 id="header" 的 <h1> 元素
- 我们使用 HTML DOM 来获得 id="header" 的元素
- JavaScript 更改此元素的内容 (innerHTML)


## 改变 HTML 属性

如需改变 HTML 元素的属性，请使用这个语法：

本例改变了 <img> 元素的 src 属性：


## 实例

实例讲解：

- 上面的 HTML 文档含有 id="image" 的 <img> 元素
- 我们使用 HTML DOM 来获得 id="image" 的元素
- JavaScript 更改此元素的属性（把 "smiley.gif" 改为 "landscape.jpg"）


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `DOM HTML` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
