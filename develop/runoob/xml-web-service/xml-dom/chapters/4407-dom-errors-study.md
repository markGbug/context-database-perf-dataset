# XML DOM：XML DOM Parse Error 对象

- 来源：[DOM ParseError Obj](https://www.runoob.com/dom/dom-errors.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：学习笔记
- 章节序号：4407

## 本章内容

微软的 parseError 对象可用于从微软的 XML 分析器取回错误信息。

要查看 Firefox 如何处理解析器错误，请看本教程的下一个页面。


## parseError 对象

在您试图打开一个 XML 文档时，就可能发生一个解析器错误（parser-error）。

通过这个 parseError 对象，您可取回错误代码、错误文本、引起错误的行等等。

注意：parseError 对象不属于 W3C DOM 标准！


## 文件错误（File Error）

在下面的代码中，我们会试图加载一个不存在的文件，并显示某些错误属性：


## 实例


## XML 错误（XML Error）

在下面的代码中，我们会让解析器加载一个形式不良的 XML 文档。

（您可以在我们的 XML 教程中阅读更多有关形式良好且有效的 XML。）


## 实例

查看 XML 文件：note_error.xml


## parseError 对象的属性


## 复习重点

- 能说明 `DOM ParseError Obj` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
