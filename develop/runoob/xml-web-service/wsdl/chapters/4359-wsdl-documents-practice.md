# WSDL：WSDL 文档

- 来源：[WSDL 文档](https://www.runoob.com/wsdl/wsdl-documents.html)
- 分类：XML / Web Service
- 技术：WSDL
- 笔记类型：练习笔记
- 章节序号：4359

## 本章内容

WSDL 文档仅仅是一个简单的 XML 文档。

它包含一系列描述某个 web service 的定义。


## WSDL 文档结构

WSDL 文档是利用这些主要的元素来描述某个 web service 的：

一个 WSDL 文档的主要结构是类似这样的：


## WSDL 文档实例

```html
<definitions>

<types>
  data type definitions........
</types>

<message>
  definition of the data being communicated....
</message>

<portType>
  set of operations......
</portType>

<binding>
  protocol and data format specification....
</binding>

</definitions>
```

WSDL 文档可包含其它的元素，比如 extension 元素，以及一个 service 元素，此元素可把若干个 web services 的定义组合在一个单一的 WSDL 文档中。


## WSDL 端口


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `WSDL 文档` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
