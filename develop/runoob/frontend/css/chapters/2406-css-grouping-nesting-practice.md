# CSS：CSS 分组 和 嵌套 选择器

- 来源：[CSS 分组和嵌套](https://www.runoob.com/css/css-grouping-nesting.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：练习笔记
- 章节序号：2406

## 本章内容

## 分组选择器

在样式表中有很多具有相同样式的元素。

```text
h1 {
    color:green;
}
h2 {
    color:green;
}
p {
    color:green;
}
```

为了尽量减少代码，你可以使用分组选择器。

每个选择器用逗号分隔。

在下面的例子中，我们对以上代码使用分组选择器：


## 实例

```text
h1,h2,p
{
    color:green;
}
```


## 嵌套选择器

它可能适用于选择器内部的选择器的样式。

在下面的例子设置了四个样式：

- p{ }: 为所有 p 元素指定一个样式。
- .marked{ }: 为所有 class="marked" 的元素指定一个样式。
- .marked p{ }: 为所有 class="marked" 元素内的 p 元素指定一个样式。
- p.marked{ }: 为所有 class="marked" 的 p 元素指定一个样式。


## 实例

```text
p
{
    color:blue;
    text-align:center;
}
.marked
{
    background-color:red;
}
.marked p
{
    color:white;
}
p.marked{
    text-decoration:underline;
}
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CSS 分组和嵌套` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
