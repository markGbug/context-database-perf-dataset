# XML Schema：XSD 杂项 数据类型

- 来源：[XML Schema 杂项数据类型](https://www.runoob.com/schema/schema-dtypes-misc.html)
- 分类：XML / Web Service
- 技术：XML Schema
- 笔记类型：练习笔记
- 章节序号：4433

## 本章内容

其他杂项数据类型包括布尔、base64Binary、十六进制、浮点、双精度、anyURI、anyURI 以及 NOTATION。


## 布尔数据类型（Boolean Data Type）

布尔数据性用于规定 true 或 false 值。

下面是一个关于某个 scheme 中逻辑声明的例子：

文档中的元素看上去应该类似这样：

注意： 合法的布尔值是 true、false、1（表示 true） 以及 0（表示 false）。


## 二进制数据类型（Binary Data Types）

二进制数据类型用于表达二进制形式的数据。

我们可使用两种二进制数据类型：

- base64Binary (Base64 编码的二进制数据)
- hexBinary (十六进制编码的二进制数据)

下面是一个关于某个 scheme 中 hexBinary 声明的例子：


## AnyURI 数据类型（AnyURI Data Type）

anyURI 数据类型用于规定 URI。

下面是一个关于某个 scheme 中 anyURI 声明的例子：

文档中的元素看上去应该类似这样：

注意： 如果某个 URI 含有空格，请用 %20 替换它们。


## 杂项数据类型


## 对杂项数据类型的限定（Restriction）

可与杂项数据类型一同使用的限定：

- enumeration (布尔数据类型无法使用此约束*)
- length (布尔数据类型无法使用此约束)
- maxLength (布尔数据类型无法使用此约束)
- minLength (布尔数据类型无法使用此约束)
- pattern
- whiteSpace

*译者注：约束指 constraint。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XML Schema 杂项数据类型` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
