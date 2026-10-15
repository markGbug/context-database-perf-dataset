# SOAP：SOAP 语法

- 来源：[SOAP 语法](https://www.runoob.com/soap/soap-syntax.html)
- 分类：XML / Web Service
- 技术：SOAP
- 笔记类型：学习笔记
- 章节序号：4343

## 本章内容

## SOAP 构建模块

一条 SOAP 消息就是一个普通的 XML 文档，包含下列元素：

- 必需的 Envelope 元素，可把此 XML 文档标识为一条 SOAP 消息
- 可选的 Header 元素，包含头部信息
- 必需的 Body 元素，包含所有的调用和响应信息
- 可选的 Fault 元素，提供有关在处理此消息所发生错误的信息

所有以上的元素均被声明于针对 SOAP 封装的默认命名空间中：

http://www.w3.org/2001/12/soap-envelope

以及针对 SOAP 编码和数据类型的默认命名空间：

http://www.w3.org/2001/12/soap-encoding


## 语法规则

这里是一些重要的语法规则：

- SOAP 消息必须用 XML 来编码
- SOAP 消息必须使用 SOAP Envelope 命名空间
- SOAP 消息必须使用 SOAP Encoding 命名空间
- SOAP 消息不能包含 DTD 引用
- SOAP 消息不能包含 XML 处理指令


## SOAP 消息的基本结构


## 复习重点

- 能说明 `SOAP 语法` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
