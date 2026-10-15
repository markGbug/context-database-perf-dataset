# XML DOM：XML DOM 解析器错误

- 来源：[DOM 解析器错误](https://www.runoob.com/dom/dom-errors-crossbrowser.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：学习笔记
- 章节序号：4408

## 本章内容

当 Firefox 遇到解析器错误，它会载入一个包含错误的 XML 文档。


## 在 Firefox 中的解析器错误

在您试图打开一个 XML 文档时，就可能发生一个解析器错误（parser-error）。

与 Internet Explorer 浏览器不同，如果 Firefox 遇到错误，它会载入包含错误描述的 XML 文档中。

XML 错误文档的根节点的名称是 "parsererror"。这是用来检查是否有错误。


## XML 错误（XML Error）

在下面的代码中，我们会让解析器加载一个形式不良的 XML 文档。

（您可以在我们的 XML 教程中阅读更多有关形式良好且有效的 XML。）


## 实例

查看 XML 文件：note_error.xml

实例解释：

- 加载 XML 文件
- 检查根节点的节点名称是否是 "parsererror"
- 把错误字符串载入变量 "errStr"
- 在错误字符串编写为 HTML 之前，把 "<" 字符替换为 "<"

注意：实际上，只有 Internet Explorer 会用 DTD 检查您的 XML，Firefox 不会。


## 跨浏览器的错误检查

在这里，我们创建了一个 XML 加载函数，在 Internet Explorer 和 Firefox 中检查解析器错误：


## 实例

查看 XML 文件：note_error.xml

实例解释 - Internet Explorer：

- 第一行创建一个空的微软 XML 文档对象。
- 第二行关闭异步加载，确保在文档完全加载之前解析器不会继续执行脚本。
- 第三行告知解析器加载名为 "note_error.xml" 的 XML 文档。
- 如果 parseError 对象的 ErrorCode 属性和 "0" 不同，提醒错误并退出函数。
- 如果 ErrorCode 属性为 "0"，返回 XML 文档。

实例解释 - Firefox：

- 第一行创建一个空的XML文档对象。
- 第二行关闭异步加载，确保在文档完全加载之前解析器不会继续执行脚本。
- 第三行告知解析器加载名为 "note_error.xml" 的 XML 文档。
- 如果返回的文档是一个错误的文档，提醒错误并退出函数。
- 如果没有，则返回 XML 文档。


## 复习重点

- 能说明 `DOM 解析器错误` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
