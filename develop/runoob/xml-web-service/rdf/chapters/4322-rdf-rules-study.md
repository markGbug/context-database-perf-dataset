# RDF：RDF 规则

- 来源：[RDF 规则](https://www.runoob.com/rdf/rdf-rules.html)
- 分类：XML / Web Service
- 技术：RDF
- 笔记类型：学习笔记
- 章节序号：4322

## 本章内容

RDF 使用 Web 标识符 (URIs) 来标识资源。

RDF 使用属性和属性值来描述资源。


## RDF 资源、属性和属性值

RDF 使用 Web 标识符来标识事物，并通过属性和属性值来描述资源。

对资源、属性和属性值的解释：

- 资源是可拥有 URI 的任何事物，比如 "https://www.runoob.com//rdf"
- 属性是拥有名称的资源，比如 "author" 或 "homepage"
- 属性值是某个属性的值，比如 "David" 或 "https://www.runoob.com/" （请注意一个属性值可以是另外一个资源）

下面的 RDF 文档可描述资源 "https://www.runoob.com//rdf"：

上面是一个简化的例子。命名空间被忽略了。


## RDF 陈述

资源、属性和属性值的组合可形成一个陈述（被称为陈述的主体、谓语和客体）。

请看一些陈述的具体例子，来加深理解：

陈述："The author of https://www.runoob.com//rdf is David."

- 陈述的主体是：https://www.runoob.com//rdf
- 谓语是：author
- 客体是：David

陈述："The homepage of https://www.runoob.com//rdf is https://www.runoob.com/".

- 陈述的主体是：https://www.runoob.com//rdf
- 谓语是：homepage
- 客体是：https://www.runoob.com/


## 复习重点

- 能说明 `RDF 规则` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
