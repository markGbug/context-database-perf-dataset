# RDF：RDF Schema (RDFS)

- 来源：[RDF Schema](https://www.runoob.com/rdf/rdf-schema.html)
- 分类：XML / Web Service
- 技术：RDF
- 笔记类型：练习笔记
- 章节序号：4327

## 本章内容

RDF Schema (RDFS) 是对 RDF 的一种扩展。


## RDF Schema 和 应用程序的类

RDF 通过类、属性和值来描述资源。

此外，RDF 还需要一种定义应用程序专业的类和属性的方法。应用程序专用的类和属性必须使用对 RDF 的扩展来定义。

RDF Schema 就是这样一种扩展。


## RDF Schema (RDFS)

RDF Schema 不提供实际的应用程序专用的类和属性，而是提供了描述应用程序专用的类和属性的框架。

RDF Schema 中的类与面向对象编程语言中的类非常相似。这就使得资源能够作为类的实例和类的子类来被定义。


## RDFS 实例

下面的实例演示了 RDFS 的能力的某些方面：

在上面的例子中，资源 "horse" 是类 "animal" 的子类。


## 简写的例子

由于一个 RDFS 类就是一个 RDF 资源，我们可以通过使用 rdfs:Class 取代 rdf:Description，并去掉 rdf:type 信息，来把上面的例子简写一下：

就是这样！


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `RDF Schema` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
