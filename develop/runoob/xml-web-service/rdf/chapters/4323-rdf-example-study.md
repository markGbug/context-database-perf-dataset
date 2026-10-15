# RDF：RDF 实例

- 来源：[RDF 实例](https://www.runoob.com/rdf/rdf-example.html)
- 分类：XML / Web Service
- 技术：RDF
- 笔记类型：学习笔记
- 章节序号：4323

## 本章内容

## RDF 实例

这是一个 CD 列表的其中几行:

这是一个 RDF 文档的其中几行：

此 RDF 文档的第一行是 XML 声明。这个 XML 声明之后是 RDF 文档的根元素：<rdf:RDF>。

xmlns:rdf 命名空间，规定了带有前缀 rdf 的元素来自命名空间 "http://www.w3.org/1999/02/22-rdf-syntax-ns#"。

xmlns:cd 命名空间，规定了带有前缀 cd 的元素来自命名空间 "http://www.recshop.fake/cd#"。

<rdf:Description> 元素包含了对被 rdf:about 属性标识的资源的描述。

元素：<cd:artist>、<cd:country>、<cd:company> 等是此资源的属性。


## RDF 在线验证器

W3C 的 RDF 验证服务在您学习 RDF 时是很有帮助的。在此您可对 RDF 文件进行试验。

RDF 在线验证器可解析您的 RDF 文档，检查其中的语法，并为您的 RDF 文档生成表格和图形视图。

把下面这个例子拷贝粘贴到 W3C 的 RDF 验证器：

在您对上面的例子进行解析后，结果将是类似这样的。


## 复习重点

- 能说明 `RDF 实例` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
