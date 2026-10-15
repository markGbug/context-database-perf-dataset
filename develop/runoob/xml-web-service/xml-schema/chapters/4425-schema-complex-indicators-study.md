# XML Schema：XSD 指示器

- 来源：[XML Schema 指示器](https://www.runoob.com/schema/schema-complex-indicators.html)
- 分类：XML / Web Service
- 技术：XML Schema
- 笔记类型：学习笔记
- 章节序号：4425

## 本章内容

通过指示器，我们可以控制在文档中使用元素的方式。


## 指示器

有七种指示器：

Order 指示器：

- All
- Choice
- Sequence

Occurrence 指示器：

- maxOccurs
- minOccurs

Group 指示器：

- Group name
- attributeGroup name


## Order 指示器

Order 指示器用于定义元素的顺序。


### All 指示器

<all> 指示器规定子元素可以按照任意顺序出现，且每个子元素必须只出现一次：

注意： 当使用 <all> 指示器时，你可以把 <minOccurs> 设置为 0 或者 1，而只能把 <maxOccurs> 指示器设置为 1（稍后将讲解 <minOccurs> 以及 <maxOccurs>）。


### Choice 指示器

<choice> 指示器规定可出现某个子元素或者可出现另外一个子元素（非此即彼）：


### Sequence 指示器

<sequence> 规定子元素必须按照特定的顺序出现：


## Occurrence 指示器

Occurrence 指示器用于定义某个元素出现的频率。

注意： 对于所有的 "Order" 和 "Group" 指示器（any、all、choice、sequence、group name 以及 group reference），其中的 maxOccurs 以及 minOccurs 的默认值均为 1。


### maxOccurs 指示器

<maxOccurs> 指示器可规定某个元素可出现的最大次数：

上面的例子表明，子元素 "child_name" 可在 "person" 元素中最少出现一次（其中 minOccurs 的默认值是 1），最多出现 10 次。


### minOccurs 指示器

<minOccurs> 指示器可规定某个元素能够出现的最小次数：

上面的例子表明，子元素 "child_name" 可在 "person" 元素中出现最少 0 次，最多出现 10 次。

提示：如需使某个元素的出现次数不受限制，请使用 maxOccurs="unbounded" 这个声明：


### 一个实际的例子：

名为 "Myfamily.xml" 的 XML 文件：

上面这个 XML 文件含有一个名为 "persons" 的根元素。在这个根元素内部，我们定义了三个 "person" 元素。每个 "person" 元素必须含有一个 "full_name" 元素，同时它可以包含多至 5 个 "child_name" 元素。

这是schema文件"family.xsd"：


## Group 指示器

Group 指示器用于定义相关的数批元素。


### 元素组

元素组通过 group 声明进行定义：

您必须在 group 声明内部定义一个 all、choice 或者 sequence 元素。下面这个例子定义了名为 "persongroup" 的 group，它定义了必须按照精确的顺序出现的一组元素：

在您把 group 定义完毕以后，就可以在另一个定义中引用它了：


### 属性组

属性组通过 attributeGroup 声明来进行定义：

下面这个例子定义了名为 "personattrgroup" 的一个属性组：

在您已定义完毕属性组之后，就可以在另一个定义中引用它了，就像这样：


## 复习重点

- 能说明 `XML Schema 指示器` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
