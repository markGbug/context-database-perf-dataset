# XML DOM：XML DOM - CDATASection 对象

- 来源：[DOM CDATA](https://www.runoob.com/dom/dom-cdatasection.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：练习笔记
- 章节序号：4404

## 本章内容

## 尝试一下 - 实例

下面的实例使用 XML 文件 books.xml。 外部 JavaScript 用于加载 XML 文件。

createCDATASection() - 创建一个 CDATA 区段节点


## CDATASection 对象

CDATASection 对象表示文档中的 CDATA 区段。

CDATA 区段包含了不会被解析器解析的文本。一个 CDATA 区段中的标签不会被视为标记，同时实体也不会被展开。主要的目的是为了包含诸如 XML 片段之类的材料，而无需转义所有的分隔符。

在一个 CDATA 区段中唯一被识别的分隔符是 "]]>"，它可标示 CDATA 区段的结束。CDATA 区段不能进行嵌套。


## CDATASection 对象属性


## CDATASection 对象方法


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `DOM CDATA` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
