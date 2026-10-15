# CSS：CSS3 字体

- 来源：[CSS3 字体](https://www.runoob.com/css3/css3-fonts.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：学习笔记
- 章节序号：2438

## 本章内容

## CSS3 @font-face 规则

使用以前 CSS 的版本，网页设计师不得不使用用户计算机上已经安装的字体。

使用 CSS3，网页设计师可以使用他/她喜欢的任何字体。

当你发现您要使用的字体文件时，只需简单的将字体文件包含在网站中，它会自动下载给需要的用户。

您所选择的字体在新的 CSS3 版本有关于 @font-face 规则描述。

您"自己的"的字体是在 CSS3 @font-face 规则中定义的。


## 浏览器支持

表格中的数字表示支持该属性的第一个浏览器版本号。

Internet Explorer 9+, Firefox, Chrome, Safari, 和 Opera 支持 WOFF (Web Open Font Format) 字体.

Firefox, Chrome, Safari, 和 Opera 支持 .ttf(True Type字体)和.otf(OpenType)字体字体类型）。

Chrome, Safari 和 Opera 也支持 SVG 字体/折叠.

Internet Explorer 同样支持 EOT (Embedded OpenType) 字体.

注意： Internet Explorer 8 以及更早的版本不支持新的 @font-face 规则。


## 使用您需要的字体

在新的 @font-face 规则中，您必须首先定义字体的名称（比如 myFirstFont），然后指向该字体文件。

如需为 HTML 元素使用字体，请通过 font-family 属性来引用字体的名称 (myFirstFont)：


## 实例

```html
<style>
@font-face
{
    font-family: myFirstFont;
    src: url(sansation_light.woff);
}

div
{
    font-family:myFirstFont;
}
</style>
```


## 使用粗体文本

您必须添加另一个包含粗体文字的@font-face规则：


## 实例

```text
@font-face
{
    font-family: myFirstFont;
    src: url(sansation_bold.woff);
    font-weight:bold;
}
```

该文件"Sansation_Bold.ttf"是另一种字体文件，包含Sansation字体的粗体字。

浏览器使用这一文本的字体系列"myFirstFont"时应该呈现为粗体。

这样你就可以有许多相同的字体@font-face的规则。


## CSS3 字体描述

下表列出了所有的字体描述和里面的@font-face规则定义：

- normal
- condensed
- ultra-condensed
- extra-condensed
- semi-condensed
- expanded
- semi-expanded
- extra-expanded
- ultra-expanded
- normal
- italic
- oblique
- normal
- bold
- 100
- 200
- 300
- 400
- 500
- 600
- 700
- 800
- 900


## 复习重点

- 能说明 `CSS3 字体` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
