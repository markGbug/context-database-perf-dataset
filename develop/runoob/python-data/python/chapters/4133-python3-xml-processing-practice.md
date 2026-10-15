# Python：Python3 XML 解析

- 来源：[Python3 XML 解析](https://www.runoob.com/python3/python3-xml-processing.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4133

## 本章内容

## 什么是 XML？

XML 指可扩展标记语言（eXtensible Markup Language），标准通用标记语言的子集，是一种用于标记电子文件使其具有结构性的标记语言。 你可以通过本站学习 XML 教程

XML 被设计用来传输和存储数据。

XML 是一套定义语义标记的规则，这些标记将文档分成许多部件并对这些部件加以标识。

它也是元标记语言，即定义了用于定义其他与特定领域有关的、语义的、结构化的标记语言的句法语言。


## Python 对 XML 的解析

常见的 XML 编程接口有 DOM 和 SAX，这两种接口处理 XML 文件的方式不同，当然使用场合也不同。

Python 有三种方法解析 XML：ElementTree、SAX 以及 DOM。


### 1. ElementTree

xml.etree.ElementTree 是 Python 标准库中用于处理 XML 的模块，它提供了简单而高效的 API，用于解析和生成 XML 文档。


### 2.SAX (simple API for XML )

Python 标准库包含 SAX 解析器，SAX 用事件驱动模型，通过在解析 XML 的过程中触发一个个的事件并调用用户定义的回调函数来处理 XML 文件。


### 3.DOM(Document Object Model)

将 XML 数据在内存中解析成一个树，通过对树的操作来操作 XML。

本章节使用到的 XML 实例文件 movies.xml 内容如下：


## 实例


## Python 使用 ElementTree 解析 xml

xml.etree.ElementTree 是 Python 标准库中用于处理 XML 的模块。

以下是 xml.etree.ElementTree 模块的一些关键概念和用法：

ElementTree 和 Element 对象:

- ElementTree： ElementTree 类是 XML 文档的树形表示。它包含一个或多个 Element 对象，代表整个 XML 文档。
- Element： Element 对象是 XML 文档中元素的表示。每个元素都有一个标签、一组属性和零个或多个子元素。


### 解析 XML

fromstring() 方法： 使用 fromstring() 方法可以将包含XML数据的字符串转换为 Element 对象：


## 实例

parse() 方法： 如果XML数据存储在文件中，可以使用 parse() 方法来解析整个 XML 文档：

```text
tree = ET.parse('example.xml')
root = tree.getroot()
```


### 遍历 XML 树

find() 方法： 使用 find() 方法可以查找具有指定标签的第一个子元素：

```text
title_element = root.find('title')
```

findall() 方法： 使用 findall() 方法可以查找具有指定标签的所有子元素：

```text
book_elements = root.findall('book')
```


### 访问元素的属性和文本内容

attrib 属性： 通过 attrib 属性可以访问元素的属性：

```text
price = book_element.attrib['price']
```

text 属性： 通过 text 属性可以访问元素的文本内容：

```text
title_text = title_element.text
```


### 创建 XML

Element() 构造函数： 使用 Element() 构造函数可以创建新的元素：

```text
new_element = ET.Element('new_element')
```

SubElement() 函数： 使用 SubElement() 函数可以创建具有指定标签的子元素：

```text
new_sub_element = ET.SubElement(root, 'new_sub_element')
```


### 修改 XML

修改元素的属性和文本内容： 直接修改元素的 attrib 和 text 属性。

删除元素： 使用 remove() 方法可以删除元素：

```text
root.remove(title_element)
```

简单读取 XML 内容：


## 实例

以上代码执行输出结果为：

```text
Title: Introduction to Python, Author: John Doe, Price: 29.99
Title: Data Science with Python, Author: Jane Smith, Price: 39.95
```

以下我们将创建一个包含书籍信息的XML文档，然后使用该模块进行解析和操作：


## 实例

以上实例我们首先创建一个XML文档，其中包含两本书的信息，然后，我们将这个文档保存到文件 books.xml 中，接着，我们使用 ET.parse() 方法解析文件中的XML文档，并遍历文档树，提取并打印每本书的标题、作者和价格信息。


## Python 使用 SAX 解析 xml

SAX 是一种基于事件驱动的API。

利用 SAX 解析 XML 文档牵涉到两个部分: 解析器和事件处理器。

解析器负责读取 XML 文档，并向事件处理器发送事件，如元素开始跟元素结束事件。

而事件处理器则负责对事件作出响应，对传递的 XML 数据进行处理。

- 1、对大型文件进行处理；
- 2、只需要文件的部分内容，或者只需从文件中得到特定信息。
- 3、想建立自己的对象模型的时候。

在 Python 中使用 sax 方式处理 xml 要先引入 xml.sax 中的 parse 函数，还有 xml.sax.handler 中的 ContentHandler。


### ContentHandler 类方法介绍

characters(content) 方法

调用时机：

从行开始，遇到标签之前，存在字符，content 的值为这些字符串。

从一个标签，遇到下一个标签之前， 存在字符，content 的值为这些字符串。

从一个标签，遇到行结束符之前，存在字符，content 的值为这些字符串。

标签可以是开始标签，也可以是结束标签。

startDocument() 方法

文档启动的时候调用。

endDocument() 方法

解析器到达文档结尾时调用。

startElement(name, attrs) 方法

遇到XML开始标签时调用，name 是标签的名字，attrs 是标签的属性值字典。

endElement(name) 方法

遇到XML结束标签时调用。


## make_parser 方法

以下方法创建一个新的解析器对象并返回。

```text
xml.sax.make_parser( [parser_list] )
```

参数说明:

- parser_list - 可选参数，解析器列表


## parser 方法

以下方法创建一个 SAX 解析器并解析xml文档：

```text
xml.sax.parse( xmlfile, contenthandler[, errorhandler])
```

参数说明:

- xmlfile - xml文件名
- contenthandler - 必须是一个 ContentHandler 的对象
- errorhandler - 如果指定该参数，errorhandler 必须是一个 SAX ErrorHandler 对象


## parseString 方法

parseString 方法创建一个 XML 解析器并解析 xml 字符串：

```text
xml.sax.parseString(xmlstring, contenthandler[, errorhandler])
```

参数说明:

- xmlstring - xml字符串
- contenthandler - 必须是一个 ContentHandler 的对象
- errorhandler - 如果指定该参数，errorhandler 必须是一个 SAX ErrorHandler对象


## Python 解析XML实例


## 实例

以上代码执行结果如下：

```text
*****Movie*****
Title: Enemy Behind
Type: War, Thriller
Format: DVD
Year: 2003
Rating: PG
Stars: 10
Description: Talk about a US-Japan war
*****Movie*****
Title: Transformers
Type: Anime, Science Fiction
Format: DVD
Year: 1989
Rating: R
Stars: 8
Description: A schientific fiction
*****Movie*****
Title: Trigun
Type: Anime, Action
Format: DVD
Rating: PG
Stars: 10
Description: Vash the Stampede!
*****Movie*****
Title: Ishtar
Type: Comedy
Format: VHS
Rating: PG
Stars: 2
Description: Viewable boredom
```

完整的 SAX API 文档请查阅Python SAX APIs


## 使用xml.dom解析xml

文件对象模型（Document Object Model，简称DOM），是W3C组织推荐的处理可扩展置标语言的标准编程接口。

一个 DOM 的解析器在解析一个 XML 文档时，一次性读取整个文档，把文档中所有元素保存在内存中的一个树结构里，之后你可以利用DOM 提供的不同的函数来读取或修改文档的内容和结构，也可以把修改过的内容写入xml文件。

Python 中用 xml.dom.minidom 来解析 xml 文件，实例如下：


## 实例

以上程序执行结果如下：

```text
Root element : New Arrivals
*****Movie*****
Title: Enemy Behind
Type: War, Thriller
Format: DVD
Rating: PG
Description: Talk about a US-Japan war
*****Movie*****
Title: Transformers
Type: Anime, Science Fiction
Format: DVD
Rating: R
Description: A schientific fiction
*****Movie*****
Title: Trigun
Type: Anime, Action
Format: DVD
Rating: PG
Description: Vash the Stampede!
*****Movie*****
Title: Ishtar
Type: Comedy
Format: VHS
Rating: PG
Description: Viewable boredom
```

完整的 DOM API 文档请查阅Python DOM APIs。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python3 XML 解析` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
