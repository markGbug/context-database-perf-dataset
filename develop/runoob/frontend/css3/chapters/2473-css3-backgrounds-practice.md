# CSS3：CSS3 背景

- 来源：[CSS3 背景](https://www.runoob.com/css3/css3-backgrounds.html)
- 分类：前端开发
- 技术：CSS3
- 笔记类型：练习笔记
- 章节序号：2473

## 本章内容

## CSS3 背景

CSS3 中包含几个新的背景属性，提供更大背景元素控制。

在本章您将了解以下背景属性：

- background-image
- background-size
- background-origin
- background-clip

您还将学习如何使用多重背景图像。


## 浏览器支持

表格中的数字表示支持该属性的第一个浏览器版本号。

紧跟在 -webkit-, -ms- 或 -moz- 前的数字为支持该前缀属性的第一个浏览器版本号。


## CSS3 background-image属性

CSS3中可以通过background-image属性添加背景图片。

不同的背景图像和图像用逗号隔开，所有的图片中显示在最顶端的为第一张。


## 实例

```text
#example1 {
    background-image: url(img_flwr.gif), url(paper.gif);
    background-position: right bottom, left top;
    background-repeat: no-repeat, repeat;
}
```

可以给不同的图片设置多个不同的属性


## 实例

```text
#example1 {
    background: url(img_flwr.gif) right bottom no-repeat, url(paper.gif) left top repeat;
}
```


## CSS3 background-size 属性

background-size指定背景图像的大小。CSS3以前，背景图像大小由图像的实际大小决定。

CSS3中可以指定背景图片，让我们重新在不同的环境中指定背景图片的大小。您可以指定像素或百分比大小。

你指定的大小是相对于父元素的宽度和高度的百分比的大小。


## 实例 1

重置背景图像：

```text
div
{
    background:url(img_flwr.gif);
    background-size:80px 60px;
    background-repeat:no-repeat;
}
```


## 实例 2

伸展背景图像完全填充内容区域：

```text
div
{
    background:url(img_flwr.gif);
    background-size:100% 100%;
    background-repeat:no-repeat;
}
```


## CSS3 的 background-origin 属性

background-origin 属性指定了背景图像的位置区域。

content-box, padding-box,和 border-box区域内可以放置背景图像。


## 实例

在 content-box 中定位背景图片：

```text
div
{
    background:url(img_flwr.gif);
    background-repeat:no-repeat;
    background-size:100% 100%;
    background-origin:content-box;
}
```


## CSS3 多个背景图像

CSS3 允许你在元素上添加多个背景图像。


## 实例

在 body 元素中设置两个背景图像：

```text
body
{
    background-image:url(img_flwr.gif),url(img_tree.gif);
}
```


## CSS3 background-clip属性

CSS3中background-clip背景剪裁属性是从指定位置开始绘制。


## 实例

```text
#example1 {
    border: 10px dotted black;
    padding: 35px;
    background: yellow;
    background-clip: content-box;
}
```


## 新的背景属性


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CSS3 背景` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
