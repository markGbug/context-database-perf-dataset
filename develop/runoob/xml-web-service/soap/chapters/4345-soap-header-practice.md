# SOAP：SOAP Header 元素

- 来源：[SOAP Header 元素](https://www.runoob.com/soap/soap-header.html)
- 分类：XML / Web Service
- 技术：SOAP
- 笔记类型：练习笔记
- 章节序号：4345

## 本章内容

可选的 SOAP Header 元素包含头部信息。


## SOAP Header 元素

可选的 SOAP Header 元素可包含有关 SOAP 消息的应用程序专用信息（比如认证、支付等）。

如果 Header 元素被提供，则它必须是 Envelope 元素的第一个子元素。

注意： 所有 Header 元素的直接子元素必须是合格的命名空间。

上面的例子包含了一个带有一个 "Trans" 元素的头部，它的值是 234，此元素的 "mustUnderstand" 属性的值是 "1"。

SOAP 在默认的命名空间中 ("http://www.w3.org/2001/12/soap-envelope") 定义了三个属性。

这三个属性是：actor、 mustUnderstand 以及 encodingStyle。这些被定义在 SOAP 头部的属性可定义容器如何对 SOAP 消息进行处理。


## mustUnderstand 属性

SOAP 的 mustUnderstand 属性可用于标识标题项对于要对其进行处理的接收者来说是强制的还是可选的。

假如您向 Header 元素的某个子元素添加了 "mustUnderstand="1"，则它可指示处理此头部的接收者必须认可此元素。假如此接收者无法认可此元素，则在处理此头部时必须失效。


### 语法


### 实例


## actor 属性

通过沿着消息路径经过不同的端点，SOAP 消息可从某个发送者传播到某个接收者。并非 SOAP 消息的所有部分均打算传送到 SOAP 消息的最终端点，不过，另一个方面，也许打算传送给消息路径上的一个或多个端点。

SOAP 的 actor 属性可被用于将 Header 元素寻址到一个特定的端点。


### 语法


### 实例


## encodingStyle 属性

SOAP 的 encodingStyle 属性用于定义在文档中使用的数据类型。此属性可出现在任何 SOAP 元素中，并会被应用到元素的内容及元素的所有子元素上。

SOAP 消息没有默认的编码方式。


### 语法


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SOAP Header 元素` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
