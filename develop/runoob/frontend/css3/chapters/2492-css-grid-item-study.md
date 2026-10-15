# CSS3：CSS 网格元素

- 来源：[CSS 网格元素](https://www.runoob.com/css3/css-grid-item.html)
- 分类：前端开发
- 技术：CSS3
- 笔记类型：学习笔记
- 章节序号：2492

## 本章内容

尝试一下 »


## CSS 网格元素

网格容器包含了一个或多个网格元素。

默认情况下，网格容器的每一列和每一行都有一个网格元素，我们也可以设置网格元素跨越多个列或行，行和列为行号。


### grid-column 属性

grid-column 属性定义了网格元素列的开始和结束位置。

注意： grid-column 是 grid-column-start 和 grid-column-end 属性的简写属性。

我们可以参考行号来设置网格元素，也可以使用关键字 "span" 来定义元素将跨越的列数。

以下实例设置 "item1" 在第 1 列开始，在第 5 列前结束：


## 实例

```text
.item1 {
  grid-column: 1 / 5;
}
```

以下实例设置 "item1" 跨越 3 列：


## 实例

```text
.item1 {
  grid-column: 1 / span 3;
}
```

以下实例设置 "item2" 跨越 3 列：


## 实例

```text
.item2 {
  grid-column: 2 / span 3;
}
```


### grid-row 属性

grid-row 属性定义了网格元素行的开始和结束位置。

注意： grid-row 是 grid-row-start 和 grid-row-end 属性的简写属性。

我们可以参考行号来设置网格元素，也可以使用关键字 "span" 来定义元素将跨越的行数。

以下实例设置 "item1" 在第 1 行开始，在第 4 行前结束：


## 实例

```text
.item1 {
  grid-row: 1 / 4;
}
```

以下实例设置 "item1" 跨越两行：


## 实例

```text
.item1 {
  grid-row: 1 / span 2;
}
```


### grid-area 属性

grid-area 属性是 grid-row-start, grid-column-start, grid-row-end 以及 grid-column-end 属性的简写。

以下实例设置 "item8" 从第 1 行开始和第 2 列开始， 第 5 行和第 6 列结束。


## 实例

```text
.item8 {
  grid-area: 1 / 2 / 5 / 6;
}
```

以下实例设置 "item8" 从第 2 行开始和第 1 列开始， 横跨 2 行 3 列。


## 实例

```text
.item8 {
  grid-area: 2 / 1 / span 2 / span 3;
}
```


## 复习重点

- 能说明 `CSS 网格元素` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
