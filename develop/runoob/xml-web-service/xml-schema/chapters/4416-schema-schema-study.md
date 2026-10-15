# XML Schema：XSD - <schema> 元素

- 来源：[XML schema 元素](https://www.runoob.com/schema/schema-schema.html)
- 分类：XML / Web Service
- 技术：XML Schema
- 笔记类型：学习笔记
- 章节序号：4416

## 本章内容

<schema> 元素是每一个 XML Schema 的根元素。


## <schema> 元素

<schema> 元素是每一个 XML Schema 的根元素：

<schema> 元素可包含属性。一个 schema 声明往往看上去类似这样：

以下代码片段:

显示 schema 中用到的元素和数据类型来自命名空间 "http://www.w3.org/2001/XMLSchema"。同时它还规定了来自命名空间 "http://www.w3.org/2001/XMLSchema" 的元素和数据类型应该使用前缀 xs：

这个片断：

显示被此 schema 定义的元素 (note, to, from, heading, body) 来自命名空间： "http://www.runoob.com"。

这个片断：

指出默认的命名空间是 "http://www.runoob.com"。

这个片断：

指出任何 XML 实例文档所使用的且在此 schema 中声明过的元素必须被命名空间限定。


## 在 XML 文档中引用 Schema

此 XML 文档含有对 XML Schema 的引用：

下面的代码片断：

规定了默认命名空间的声明。此声明会告知 schema 验证器，在此 XML 文档中使用的所有元素都被声明于 "http://www.runoob.com" 这个命名空间。

一旦您拥有了可用的 XML Schema 实例命名空间：

您就可以使用 schemaLocation 属性了。此属性有两个值。第一个值是需要使用的命名空间。第二个值是供命名空间使用的 XML schema 的位置：


## 复习重点

- 能说明 `XML schema 元素` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
