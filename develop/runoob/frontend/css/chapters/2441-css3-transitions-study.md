# CSS：CSS3 过渡

- 来源：[CSS3 过渡](https://www.runoob.com/css3/css3-transitions.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：学习笔记
- 章节序号：2441

## 本章内容

## CSS3 过渡

CSS3中，我们为了添加某种效果可以从一种样式转变到另一个的时候，无需使用Flash动画或JavaScript。用鼠标移过下面的元素：

用鼠标移过下面的元素：


## 浏览器支持

表格中的数字表示支持该属性的第一个浏览器版本号。

紧跟在 -webkit-, -ms- 或 -moz- 前的数字为支持该前缀属性的第一个浏览器版本号。


## 它是如何工作？

CSS3 过渡是元素从一种样式逐渐改变为另一种的效果。

要实现这一点，必须规定两项内容：

- 指定要添加效果的CSS属性
- 指定效果的持续时间。


## 实例

应用于宽度属性的过渡效果，时长为 2 秒：

```text
div
{
    transition: width 2s;
    -webkit-transition: width 2s; /* Safari */
}
```

注意： 如果未指定的期限，transition将没有任何效果，因为默认值是0。

指定的CSS属性的值更改时效果会发生变化。一个典型CSS属性的变化是用户鼠标放在一个元素上时：


## 实例

规定当鼠标指针悬浮(:hover)于 <div>元素上时：

```text
div:hover
{
    width:300px;
}
```

注意： 当鼠标光标移动到该元素时，它逐渐改变它原有样式


## 多项改变

要添加多个样式的变换效果，添加的属性由逗号分隔：


## 实例

添加了宽度，高度和转换效果：

```text
div
{
    transition: width 2s, height 2s, transform 2s;
    -webkit-transition: width 2s, height 2s, -webkit-transform 2s;
}
```


## 过渡属性

下表列出了所有的过渡属性:

下面的两个例子设置所有过渡属性：


## 实例

在一个例子中使用所有过渡属性：

```text
div
{
    transition-property: width;
    transition-duration: 1s;
    transition-timing-function: linear;
    transition-delay: 2s;
    /* Safari */
    -webkit-transition-property:width;
    -webkit-transition-duration:1s;
    -webkit-transition-timing-function:linear;
    -webkit-transition-delay:2s;
}
```


## 实例

与上面的例子相同的过渡效果，但是使用了简写的 transition 属性：

```text
div
{
    transition: width 1s linear 2s;
    /* Safari */
    -webkit-transition:width 1s linear 2s;
}
```


## 复习重点

- 能说明 `CSS3 过渡` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
