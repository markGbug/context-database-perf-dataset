# CSS：CSS 伪元素

- 来源：[CSS 伪元素](https://www.runoob.com/css/css-pseudo-elements.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：练习笔记
- 章节序号：2415

## 本章内容

CSS 伪元素是一种特殊的选择器，它可以在不改变 HTML 结构的情况下对页面元素的特定部分进行样式设置。

CSS 伪元素是用来添加一些选择器的特殊效果。

常用的 CSS 伪元素有 ::before、::after、::first-line、::first-letter 等。


## 语法

伪元素的语法：

```text
selector::pseudo-element {
    property: value;
}
```

CSS 类也可以使用伪元素：

```text
selector.class::pseudo-element {
    property: value;
}
```


## :first-line 伪元素

"first-line" 伪元素用于向文本的首行设置特殊样式。

在下面的例子中，浏览器会根据 "first-line" 伪元素中的样式对 p 元素的第一行文本进行格式化：


## 实例

```text
p:first-line
{
    color:#ff0000;
    font-variant:small-caps;
}
```

注意："first-line" 伪元素只能用于块级元素。

注意： 下面的属性可应用于 "first-line" 伪元素：

- font properties
- color properties
- background properties
- word-spacing
- letter-spacing
- text-decoration
- vertical-align
- text-transform
- line-height
- clear


## :first-letter 伪元素

"first-letter" 伪元素用于向文本的首字母设置特殊样式：


## 实例

```text
p:first-letter
{
    color:#ff0000;
    font-size:xx-large;
}
```

注意： "first-letter" 伪元素只能用于块级元素。

注意： 下面的属性可应用于 "first-letter" 伪元素：

- font properties
- color properties
- background properties
- margin properties
- padding properties
- border properties
- text-decoration
- vertical-align (only if "float" is "none")
- text-transform
- line-height
- float
- clear


## 伪元素和CSS类

伪元素可以结合CSS类：

```html
p.article:first-letter {color:#ff0000;}

<p class="article">文章段落</p>
```

上面的例子会使所有 class 为 article 的段落的首字母变为红色。


## 多个伪元素

可以结合多个伪元素来使用。

在下面的例子中，段落的第一个字母将显示为红色，其字体大小为 xx-large。第一行中的其余文本将为蓝色，并以小型大写字母显示。

段落中的其余文本将以默认字体大小和颜色来显示：


## 实例

```text
p:first-letter
{
    color:#ff0000;
    font-size:xx-large;
}
p:first-line
{
    color:#0000ff;
    font-variant:small-caps;
}
```


## CSS - :before 伪元素

":before" 伪元素可以在元素的内容前面插入新内容。

下面的例子在每个 <h1>元素前面插入一幅图片：


## 实例

```text
h1:before
{
    content:url(smiley.gif);
}
```


## CSS - :after 伪元素

":after" 伪元素可以在元素的内容之后插入新内容。

下面的例子在每个 <h1> 元素后面插入一幅图片：


## 实例

```text
h1:after
{
    content:url(smiley.gif);
}
```


## 所有CSS伪类/元素


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CSS 伪元素` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
