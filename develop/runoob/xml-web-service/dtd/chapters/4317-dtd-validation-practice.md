# DTD：DTD 验证

- 来源：[DTD 验证](https://www.runoob.com/dtd/dtd-validation.html)
- 分类：XML / Web Service
- 技术：DTD
- 笔记类型：练习笔记
- 章节序号：4317

## 本章内容

使用 Internet Explorer 可根据某个 DTD 来验证您的 XML。


## 通过 XML 解析器进行验证

当您试图打开某个 XML 文档时，XML 解析器有可能会产生错误。通过访问 parseError 对象，就可以取回引起错误的确切代码、文本甚至所在的行。

注意： load() 方法用于文件，而 loadXML() 方法用于字符串。


## 实例

查看xml文件


## 关闭验证

通过把 XML 解析器的 validateOnParse 设置为 "false"，就可以关闭验证。


## 实例


## 通用的 XML 验证器

为了帮助您验证 XML 文件，我们创建了此 链接，这样你就可以验证任何 XML 文件了。


## parseError 对象

您可以在我们的《XML DOM 教程》中阅读更多有关 parseError 对象的信息。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `DTD 验证` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
