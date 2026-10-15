# SOAP：SOAP Envelope 元素

- 来源：[SOAP Envelope 元素](https://www.runoob.com/soap/soap-envelope.html)
- 分类：XML / Web Service
- 技术：SOAP
- 笔记类型：练习笔记
- 章节序号：4344

## 本章内容

强制使用的 SOAP 的 Envelope 元素是 SOAP 消息的根元素。


## SOAP Envelope 元素

必需的 SOAP 的 Envelope 元素是 SOAP 消息的根元素。它可把 XML 文档定义为 SOAP 消息。


### 实例

```html
<?xml version="1.0"?>
<soap:Envelope
xmlns:soap="http://www.w3.org/2001/12/soap-envelope"
soap:encodingStyle="http://www.w3.org/2001/12/soap-encoding">
  ...
  Message information goes here
  ...
</soap:Envelope>
```


## xmlns:soap 命名空间

SOAP 消息必须拥有与命名空间 "http://www.w3.org/2001/12/soap-envelope" 相关联的一个 Envelope 元素。

如果使用了不同的命名空间，应用程序会发生错误，并抛弃此消息。


## encodingStyle 属性

SOAP 的 encodingStyle 属性用于定义在文档中使用的数据类型。此属性可出现在任何 SOAP 元素中，并会被应用到元素的内容及元素的所有子元素上。

SOAP 消息没有默认的编码方式。


### 语法

```text
soap:encodingStyle="URI"
```


### 实例

```html
<?xml version="1.0"?>
<soap:Envelope
xmlns:soap="http://www.w3.org/2001/12/soap-envelope"
soap:encodingStyle="http://www.w3.org/2001/12/soap-encoding">
  ...
  Message information goes here
  ...
</soap:Envelope>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SOAP Envelope 元素` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
