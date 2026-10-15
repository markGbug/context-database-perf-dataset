# XPath：XPath 语法

- 来源：[XPath 语法](https://www.runoob.com/xpath/xpath-syntax.html)
- 分类：XML / Web Service
- 技术：XPath
- 笔记类型：学习笔记
- 章节序号：4469

## 本章内容

XPath 使用路径表达式来选取 XML 文档中的节点或节点集。节点是通过沿着路径 (path) 或者步 (steps) 来选取的。


## XML 实例文档

我们将在下面的例子中使用这个 XML 文档。


## 实例

```html
<?xml version="1.0" encoding="UTF-8"?>

<bookstore>

<book>
  <title lang="eng">Harry Potter</title>
  <price>29.99</price>
</book>

<book>
  <title lang="eng">Learning XML</title>
  <price>39.95</price>
</book>

</bookstore>
```


## 选取节点

XPath 使用路径表达式在 XML 文档中选取节点。节点是通过沿着路径或者 step 来选取的。 下面列出了最有用的路径表达式：

在下面的表格中，我们已列出了一些路径表达式以及表达式的结果：

选取根元素 bookstore。

注释：假如路径起始于正斜杠( / )，则此路径始终代表到某元素的绝对路径！


## 谓语（Predicates）

谓语用来查找某个特定的节点或者包含某个指定的值的节点。

谓语被嵌在方括号中。

在下面的表格中，我们列出了带有谓语的一些路径表达式，以及表达式的结果：


## 选取未知节点

XPath 通配符可用来选取未知的 XML 元素。

在下面的表格中，我们列出了一些路径表达式，以及这些表达式的结果：


## 选取若干路径

通过在路径表达式中使用"|"运算符，您可以选取若干个路径。

在下面的表格中，我们列出了一些路径表达式，以及这些表达式的结果：


## 复习重点

- 能说明 `XPath 语法` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
