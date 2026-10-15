# XPath：XPath、XQuery 以及 XSLT 函数函数参考手册

- 来源：[XPath、XQuery 以及 XSLT 函数](https://www.runoob.com/xpath/xpath-functions.html)
- 分类：XML / Web Service
- 技术：XPath
- 笔记类型：学习笔记
- 章节序号：4474

## 本章内容

下面的参考手册定义了XPath 2.0，XQuery 1.0和XSLT 2.0中的函数。

- 存取
- 错误和跟踪
- 数值
- 字符串
- AnyURI
- 逻辑
- 持续时间/日期/时间
- QName
- 节点
- 序列
- Context

函数命名空间的默认前缀为 fn:

函数命名空间的 URI为 : http://www.w3.org/2005/xpath-functions


### 存取函数

- fn:base-uri()
- fn:base-uri(node)


### 错误和跟踪函数

- fn:error()
- fn:error(error)
- fn:error(error,description)
- fn:error(error,description,error-object)

例子：error(fn:QName('http://example.com/test', 'err:toohigh'), 'Error: Price is too high')

结果：向外部处理环境返回 http://example.com/test#toohigh 以及字符串 "Error: Price is too high"。


### 有关数值的函数

返回参数的数值。参数可以是布尔值、字符串或节点集。

例子：number('100')

结果：100

返回参数的绝对值。

例子：abs(3.14)

结果：3.14

例子：abs(-3.14)

结果：3.14

返回大于 num 参数的最小整数。

例子：ceiling(3.14)

结果：4

返回不大于 num 参数的最大整数。

例子：floor(3.14)

结果：3

把 num 参数舍入为最接近的整数。

例子：round(3.14)

结果：3

例子：round-half-to-even(0.5)

结果：0

例子：round-half-to-even(1.5)

结果：2

例子：round-half-to-even(2.5)

结果：2


### 有关字符串的函数

返回参数的字符串值。参数可以是数字、逻辑值或节点集。

例子：string(314)

结果："314"

根据代码点序列返回字符串。

例子：codepoints-to-string(84, 104, 233, 114, 232, 115, 101)

结果：'Thérèse'

根据字符串返回代码点序列。

例子：string-to-codepoints("Thérèse")

结果：84, 104, 233, 114, 232, 115, 101

- fn:compare(comp1,comp2)
- fn:compare(comp1,comp2,collation)

如果 comp1 小于 comp2，则返回 -1。如果 comp1 等于 comp2，则返回 0。如果 comp1 大于 comp2，则返回 1。（根据所用的对照规则）。

例子：compare('ghi', 'ghi')

结果：0

返回字符串的拼接。

例子：concat('XPath ','is ','FUN!')

结果：'XPath is FUN!'

使用 sep 参数作为分隔符，来返回 string 参数拼接后的字符串。

例子：string-join(('We', 'are', 'having', 'fun!'), ' ')

结果：' We are having fun! '

例子：string-join(('We', 'are', 'having', 'fun!'))

结果：'Wearehavingfun!'

例子：string-join((), 'sep')

结果：''

- fn:substring(string,start,len)
- fn:substring(string,start)

返回从 start 位置开始的指定长度的子字符串。第一个字符的下标是 1。如果省略 len 参数，则返回从位置 start 到字符串末尾的子字符串。

例子：substring('Beatles',1,4)


### 针对 anyURI 的函数


### 关于布尔值的函数

首先通过 boolean() 函数把参数还原为一个布尔值。如果该布尔值为 false，则返回 true，如果该布尔值为 true，则返回 false。

例子：not(true())

结果：false

返回布尔值 true。

例子：true()

结果：true

返回布尔值 false。

例子：false()

结果：false


### 有关持续时间、日期和时间的函数

日期、时间、持续时间的组件提取函数

返回参数本地值的年部分的整数。

例子：year-from-dateTime(xs:dateTime("2005-01-10T12:30-04:10"))

结果：2005

返回参数本地值的月部分的整数。

例子：month-from-dateTime(xs:dateTime("2005-01-10T12:30-04:10"))

结果：01

返回参数本地值的天部分的整数。

例子：day-from-dateTime(xs:dateTime("2005-01-10T12:30-04:10"))

结果：10

返回参数本地值的小时部分的整数。

例子：hours-from-dateTime(xs:dateTime("2005-01-10T12:30-04:10"))

结果：12

返回参数本地值的分钟部分的整数。

例子：minutes-from-dateTime(xs:dateTime("2005-01-10T12:30-04:10"))

结果：30

返回参数本地值的秒部分的十进制数。

例子：seconds-from-dateTime(xs:dateTime("2005-01-10T12:30:00-04:10"))

结果：0

返回参数本地值中表示年的整数。

例子：year-from-date(xs:date("2005-04-23"))

结果：2005

返回参数本地值中表示月的整数。

例子：month-from-date(xs:date("2005-04-23"))

结果：4

返回参数本地值中表示天的整数。

例子：day-from-date(xs:date("2005-04-23"))

结果：23


### 与 QNames 相关的函数


### 关于节点的函数

- fn:name()
- fn:name(nodeset)
- fn:local-name()
- fn:local-name(nodeset)
- fn:namespace-uri()
- fn:namespace-uri(nodeset)

如果当前节点的语言匹配指定的语言，则返回 true。

例子：Lang("en") is true for <p xml:lang="en">...</p>

例子：Lang("de") is false for <p xml:lang="en">...</p>

- fn:root()
- fn:root(node)


### 有关序列的函数


### 一般性的函数

返回在项目序列中等于 searchitem 参数的位置。

例子：index-of ((15, 40, 25, 40, 10), 40)

结果：(2, 4)

例子：index-of (("a", "dog", "and", "a", "duck"), "a")

Result (1, 4)

例子：index-of ((15, 40, 25, 40, 10), 18)

结果：()

返回由 item 参数构造的新序列 - 同时删除 position 参数指定的项目。

例子：remove(("ab", "cd", "ef"), 0)

结果：("ab", "cd", "ef")

例子：remove(("ab", "cd", "ef"), 1)

结果：("cd", "ef")

例子：remove(("ab", "cd", "ef"), 4)

结果：("ab", "cd", "ef")

如果参数值是空序列，则返回 true，否则返回 false。

例子：empty(remove(("ab", "cd"), 1))

结果：false

如果参数值不是空序列，则返回 true，否则返回 false。

例子：exists(remove(("ab"), 1))

结果：false

返回唯一不同的值。

例子：distinct-values((1, 2, 3, 1, 2))

结果：(1, 2, 3)

返回由 item 参数构造的新序列 - 同时在 pos 参数指定位置插入 inserts 参数的值。

例子：insert-before(("ab", "cd"), 0, "gh")

结果：("gh", "ab", "cd")

例子：insert-before(("ab", "cd"), 1, "gh")

结果：("gh", "ab", "cd")


### 测试序列容量的函数


### Equals, Union, Intersection and Except


### 合计函数


### 生成序列的函数

- fn:collection()
- fn:collection(string)


### 上下文函数

返回当前正在被处理的节点的 index 位置。

例子：//book[position()<=3]

结果：选择前三个 book 元素

返回在被处理的节点列表中的项目数目。

例子：//book[last()]

结果：选择最后一个 book 元素


## 复习重点

- 能说明 `XPath、XQuery 以及 XSLT 函数` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
