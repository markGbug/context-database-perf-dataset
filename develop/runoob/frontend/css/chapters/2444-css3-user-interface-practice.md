# CSS：CSS3 用户界面

- 来源：[CSS3 用户界面](https://www.runoob.com/css3/css3-user-interface.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：练习笔记
- 章节序号：2444

## 本章内容

## CSS3 用户界面

在 CSS3 中, 增加了一些新的用户界面特性来调整元素尺寸，框尺寸和外边框。

在本章中，您将了解以下的用户界面属性：

- resize
- box-sizing
- outline-offset


## 浏览器支持

表格中的数字表示支持该属性的第一个浏览器版本号。

紧跟在 -webkit-, -ms- 或 -moz- 前的数字为支持该前缀属性的第一个浏览器版本号。


## CSS3 调整尺寸(Resizing)

CSS3中，resize属性指定一个元素是否应该由用户去调整大小。

CSS代码如下：


## 实例

由用户指定一个div元素尺寸大小：

```text
div {
    resize:both;
    overflow:auto;
}
```


## CSS3 方框大小调整(Box Sizing)

box-sizing 属性允许您以确切的方式定义适应某个区域的具体内容。


## 实例

规定两个并排的带边框方框：

```text
div
{
    box-sizing:border-box;
    -moz-box-sizing:border-box; /* Firefox */
    width:50%;
    float:left;
}
```


## CSS3 外形修饰（outline-offset ）

outline-offset 属性对轮廓进行偏移，并在超出边框边缘的位置绘制轮廓。

轮廓与边框有两点不同：

- 轮廓不占用空间
- 轮廓可能是非矩形

CSS 代码如下:


## 实例

规定边框边缘之外 15 像素处的轮廓：

```text
div
{
    border:2px solid black;
    outline:2px solid red;
    outline-offset:15px;
}
```


## 新的用户界面特性


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CSS3 用户界面` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
