# CSS：CSS margin(外边距)

- 来源：[CSS margin(外边距)](https://www.runoob.com/css/css-margin.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：练习笔记
- 章节序号：2404

## 本章内容

CSS margin(外边距)属性定义元素周围的空间。


## margin

margin 清除周围的（外边框）元素区域。margin 没有背景颜色，是完全透明的。

margin 可以单独改变元素的上，下，左，右边距，也可以一次改变所有的属性。


## 可能的值

Margin可以使用负值，重叠的内容。


## Margin - 单边外边距属性

在CSS中，它可以指定不同的侧面不同的边距：


## 实例

```text
margin-top:100px;
margin-bottom:100px;
margin-right:50px;
margin-left:50px;
```


## Margin - 简写属性

为了缩短代码，有可能使用一个属性中margin指定的所有边距属性。这就是所谓的简写属性。

所有边距属性的简写属性是 margin :


## 实例

```text
margin:100px 50px;
```

margin属性可以有一到四个值。

- margin:25px 50px 75px 100px; 上边距为25px 右边距为50px 下边距为75px 左边距为100px
- margin:25px 50px 75px; 上边距为25px 左右边距为50px 下边距为75px
- margin:25px 50px; 上下边距为25px 左右边距为50px
- margin:25px;所有的4个边距都是25px


## 更多实例

文本的上边距设置使用厘米值 这个例子演示了如何设置一个使用厘米值的文本的顶部margin。

Set 使用百分比值设置文本的下边距 这个例子演示了如何设置使用百分比值的下边距，相对于包含的元素的宽度。


## 所有的CSS边距属性


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CSS margin(外边距)` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
