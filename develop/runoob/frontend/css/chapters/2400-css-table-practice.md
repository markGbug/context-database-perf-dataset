# CSS：CSS 表格

- 来源：[CSS Table(表格)](https://www.runoob.com/css/css-table.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：练习笔记
- 章节序号：2400

## 本章内容

使用 CSS 可以使 HTML 表格更美观。


## 表格边框

指定CSS表格边框，使用border属性。

下面的例子指定了一个表格的Th和TD元素的黑色边框：


## 实例

```text
table, th, td
{
    border: 1px solid black;
}
```

请注意，在上面的例子中的表格有双边框。这是因为表和th/ td元素有独立的边界。

为了显示一个表的单个边框，使用 border-collapse属性。


## 折叠边框

border-collapse 属性设置表格的边框是否被折叠成一个单一的边框或隔开：


## 实例

```text
table
{
    border-collapse:collapse;
}
table,th, td
{
    border: 1px solid black;
}
```


## 表格宽度和高度

Width和height属性定义表格的宽度和高度。

下面的例子是设置100％的宽度，50像素的th元素的高度的表格：


## 实例

```text
table
{
    width:100%;
}
th
{
    height:50px;
}
```


## 表格文字对齐

表格中的文本对齐和垂直对齐属性。

text-align属性设置水平对齐方式，向左，右，或中心：


## 实例

```text
td
{
    text-align:right;
}
```

垂直对齐属性设置垂直对齐，比如顶部，底部或中间：


## 实例

```text
td
{
    height:50px;
    vertical-align:bottom;
}
```


## 表格填充

如需控制边框和表格内容之间的间距，应使用td和th元素的填充属性：


## 实例

```text
td
{
    padding:15px;
}
```


## 表格颜色

下面的例子指定边框的颜色，和th元素的文本和背景颜色：


## 实例

```text
table, td, th
{
    border:1px solid green;
}
th
{
    background-color:green;
    color:white;
}
```


## 更多实例

制作一个个性表格 这个例子演示了如何创建一个个性的表格。

设置表格标题的位置 这个例子演示了如何定位表格标题。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CSS Table(表格)` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
