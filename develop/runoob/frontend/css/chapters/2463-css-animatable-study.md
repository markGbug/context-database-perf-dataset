# CSS：CSS 动画

- 来源：[CSS 动画](https://www.runoob.com/cssref/css-animatable.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：学习笔记
- 章节序号：2463

## 本章内容

## 定义和用法

一些 CSS 属性是可以有动画效果的，这意味着它们可以用于动画和过渡。

动画属性可以逐渐地从一个值变化到另一个值，比如尺寸大小、数量、百分比和颜色。


## 浏览器支持

表格中的数字表示支持该方法的第一个浏览器的版本号。

紧跟在数字后面的 -webkit-, -moz-, 或 -o- 指定了第一个支持该属性的浏览器版本前缀。


## 实例

背景颜色逐渐地从红色变化到蓝色：

```text
@keyframes mymove
    {
    from {background-color:red;}
    to {background-color:blue;}
}

/*Safari 和 Chrome:*/
@-webkit-keyframes mymove
{
    from {background-color:red;}
    to {background-color:blue;}
}
```


## 动画属性

CSS 中的动画属性：


## 复习重点

- 能说明 `CSS 动画` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
