# CSS：CSS 文本格式

- 来源：[CSS Text(文本)](https://www.runoob.com/css/css-text.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：学习笔记
- 章节序号：2396

## 本章内容

This text is styled with some of the text formatting properties. The heading uses the text-align, text-transform, and color properties. The paragraph is indented, aligned, and the space between characters is specified. The underline is removed from the "尝试一下" link.


## 文本颜色

颜色属性被用来设置文字的颜色。

颜色是通过CSS最经常的指定：

- 十六进制值 - 如: ＃FF0000
- 一个RGB值 - 如: RGB(255,0,0)
- 颜色的名称 - 如: red

参阅 CSS 颜色值 查看完整的颜色值。

一个网页的背景颜色是指在主体内的选择：


## 实例

```text
body {color:red;}
h1 {color:#00ff00;}
h2 {color:rgb(255,0,0);}
```

对于W3C标准的CSS：如果你定义了颜色属性，你还必须定义背景色属性。


## 文本的对齐方式

文本排列属性是用来设置文本的水平对齐方式。

文本可居中或对齐到左或右,两端对齐.

当text-align设置为"justify"，每一行被展开为宽度相等，左，右外边距是对齐（如杂志和报纸）。


## 实例

```text
h1 {text-align:center;}
p.date {text-align:right;}
p.main {text-align:justify;}
```


## 文本修饰

text-decoration 属性用来设置或删除文本的装饰。

从设计的角度看 text-decoration属性主要是用来删除链接的下划线：


## 实例

```text
a {text-decoration:none;}
```

也可以这样装饰文字：


## 实例

```text
h1 {text-decoration:overline;}
h2 {text-decoration:line-through;}
h3 {text-decoration:underline;}
```

我们不建议强调指出不是链接的文本，因为这常常混淆用户。


## 文本转换

文本转换属性是用来指定在一个文本中的大写和小写字母。

可用于所有字句变成大写或小写字母，或每个单词的首字母大写。


## 实例

```text
p.uppercase {text-transform:uppercase;}
p.lowercase {text-transform:lowercase;}
p.capitalize {text-transform:capitalize;}
```


## 文本缩进

文本缩进属性是用来指定文本的第一行的缩进。


## 实例

```text
p {text-indent:50px;}
```


## 更多实例

指定字符之间的空间 这个例子演示了如何增加或减少字符之间的空间。

指定行与行之间的空间 这个例子演示了如何指定在一个段落中行之间的空间

设置元素的文本方向 这个例子演示了如何改变元素的文本方向。

增加单词之间的空白空间 这个例子演示了如何增加一个段落中的单词之间的空白空间。

在元素内禁用文字不换行 这个例子演示了如何禁用一个元素内的文字不换行。

垂直对齐图像 这个例子演示了如何设置文本的垂直对齐图像。

添加文本阴影 这个例子演示了如何设置文本阴影。


## 所有CSS文本属性。


## 复习重点

- 能说明 `CSS Text(文本)` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
