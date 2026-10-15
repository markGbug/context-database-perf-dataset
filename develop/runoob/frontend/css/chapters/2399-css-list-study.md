# CSS：CSS 列表

- 来源：[CSS 列表](https://www.runoob.com/css/css-list.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：学习笔记
- 章节序号：2399

## 本章内容

CSS 列表属性作用如下：

- 设置不同的列表项标记为有序列表
- 设置不同的列表项标记为无序列表
- 设置列表项标记为图像


## 列表

在 HTML中，有两种类型的列表：

- 无序列表 ul - 列表项标记用特殊图形（如小黑点、小方框等）
- 有序列表 ol - 列表项的标记有数字或字母

使用 CSS，可以列出进一步的样式，并可用图像作列表项标记。


### 无序列表如下所示:

- Coffee
- Tea
- Coca Cola
- Coffee
- Tea
- Coca Cola


### 有序列表如下所示:

- Coffee
- Tea
- Coca Cola
- Coffee
- Tea
- Coca Cola


## 不同的列表项标记

list-style-type属性指定列表项标记的类型是：


## 实例

```text
ul.a {list-style-type: circle;}
ul.b {list-style-type: square;}

ol.c {list-style-type: upper-roman;}
ol.d {list-style-type: lower-alpha;}
```

一些值是无序列表，以及有些是有序列表。


## 作为列表项标记的图像

要指定列表项标记的图像，使用列表样式图像属性：


## 实例

```text
ul
{
    list-style-image: url('sqpurple.gif');
}
```

上面的例子在所有浏览器中显示并不相同，IE 和 Opera 显示图像标记比火狐，Chrome 和 Safari更高一点点。

如果你想在所有的浏览器放置同样的形象标志，就应使用浏览器兼容性解决方案，过程如下


## 浏览器兼容性解决方案

同样在所有的浏览器，下面的例子会显示的图像标记：


## 实例

```text
ul
{
    list-style-type: none;
    padding: 0px;
    margin: 0px;
}
ul li
{
    background-image: url(sqpurple.gif);
    background-repeat: no-repeat;
    background-position: 0px 5px;
    padding-left: 14px;
}
```

例子解释：

- ul: 设置列表类型为没有列表项标记 设置填充和边距 0px（浏览器兼容性）
- ul 中所有 li: 设置图像的 URL，并设置它只显示一次（无重复） 您需要的定位图像位置（左 0px 和上下 5px） 用 padding-left 属性把文本置于列表中


## 列表 - 简写属性

在单个属性中可以指定所有的列表属性。这就是所谓的简写属性。

为列表使用简写属性，列表样式属性设置如下：


## 实例

```text
ul
{
    list-style: square url("sqpurple.gif");
}
```

可以按顺序设置如下属性：

- list-style-type
- list-style-position (有关说明，请参见下面的CSS属性表)
- list-style-image

如果上述值丢失一个，其余仍在指定的顺序，就没关系。


## 更多实例

所有不同的列表项标记 这个例子演示了所有不同的 CSS 列表项标记。


## 移除默认设置

list-style-type:none 属性可以用于移除小标记。默认情况下列表 <ul> 或 <ol> 还设置了内边距和外边距，可使用 margin:0 和 padding:0 来移除:


## 实例

```text
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
```


## 所有的CSS列表属性


## 复习重点

- 能说明 `CSS 列表` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
