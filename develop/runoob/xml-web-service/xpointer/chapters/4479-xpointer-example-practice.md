# XPointer：XPointer 实例

- 来源：[XPointer 实例](https://www.runoob.com/xlink/xpointer-example.html)
- 分类：XML / Web Service
- 技术：XPointer
- 笔记类型：练习笔记
- 章节序号：4479

## 本章内容

让我们通过研究一个实例来学习一些基础的 XPointer 语法。


## XPointer 实例

在本例中，我们会为您展示如何使用 XPointer 并结合 XLink 来指向另外一个文档的某个具体的部分。

我们将通过研究目标 XML 文档开始（即我们要链接的那个文档）。


## 目标XML文档

目标XML文档名为 "dogbreeds.xml"，它列出了一些不同的狗种类：

在您的浏览器查看 "dogbreeds.xml" 文件。

注意上面的 XML 文档在每个我们需要链接的元素上使用了 id 属性！


## XML 链接文档

不止能够链接到整个文档（当使用 XLink 时），XPointer 允许您链接到文档的特定部分。如需链接到页面的某个具体的部分，请在 xlink:href 属性中的 URL 后添加一个井号 (#) 以及一个 XPointer 表达式。

表达式：#xpointer(id("Rottweiler")) 可引用目标文档中 id 值为 "Rottweiler" 的元素。

因此，xlink:href 属性会类似这样：xlink:href="http://dog.com/dogbreeds.xml#xpointer(id('Rottweiler'))"

不过，当使用 id 链接到某个元素时，XPointer 允许简写形式。您可以直接使用 id 的值，就像这样：xlink:href="http://dog.com/dogbreeds.xml#Rottweiler"。

下面的 XML 文档可引用每条狗的品种信息，均通过 XLink 和 XPointer 来引用：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XPointer 实例` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
