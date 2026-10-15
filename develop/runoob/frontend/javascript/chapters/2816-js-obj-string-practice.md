# JavaScript：JavaScript 字符串（String） 对象

- 来源：[JavaScript String](https://www.runoob.com/js/js-obj-string.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：练习笔记
- 章节序号：2816

## 本章内容

String 对象用于处理已有的字符块。


## JavaScript 字符串

一个字符串用于存储一系列字符就像 "John Doe".

一个字符串可以使用单引号或双引号：


## 实例

你使用位置（索引）可以访问字符串中任何的字符：


## 实例

字符串的索引从零开始, 所以字符串第一字符为 [0],第二个字符为 [1], 等等。

你可以在字符串中使用引号，如下实例：


## 实例

或者你可以在字符串中使用转义字符(\)使用引号：


## 实例


## 字符串（String）

字符串（String）使用长度属性length来计算字符串的长度：


## 实例


## 在字符串中查找字符串

字符串使用 indexOf() 来定位字符串中某一个指定的字符首次出现的位置：


## 实例

如果没找到对应的字符函数返回-1

lastIndexOf() 方法在字符串末尾开始查找字符串出现的位置。


## 内容匹配

match()函数用来查找字符串中特定的字符，并且如果找到的话，则返回这个字符。


## 实例


## 替换内容

replace() 方法在字符串中用某些字符替换另一些字符。


## 实例


## 字符串大小写转换

字符串大小写转换使用函数 toUpperCase() / toLowerCase():


## 实例


## 字符串转为数组

字符串使用split()函数转为数组:


## 实例


## 特殊字符

Javascript 中可以使用反斜线（\）插入特殊符号，如：撇号,引号等其他特殊符号。

查看如下 JavaScript 代码:

在JavaScript中，字符串的开始和停止使用单引号或双引号。这意味着，上面的字符串将被切成： We are the so-called

解决以上的问题可以使用反斜线来转义引号：

JavaScript将输出正确的文本字符串：We are the so-called "Vikings" from the north.

下表列出其他特殊字符，可以使用反斜线转义特殊字符：


## 字符串属性和方法

属性:

- length
- prototype
- constructor

方法:

- charAt()
- charCodeAt()
- concat()
- fromCharCode()
- indexOf()
- lastIndexOf()
- match()
- replace()
- search()
- slice()
- split()
- substr()
- substring()
- toLowerCase()
- toUpperCase()
- valueOf()

更多方法与属性介绍可以参考：JavaScript String 对象


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `JavaScript String` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
