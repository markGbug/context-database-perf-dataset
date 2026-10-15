# CSS3：CSS 网格容器

- 来源：[CSS 网格容器](https://www.runoob.com/css3/css-grid-container.html)
- 分类：前端开发
- 技术：CSS3
- 笔记类型：学习笔记
- 章节序号：2491

## 本章内容

尝试一下 »


## 网格容器

要使 HTML 元素变成一个网格容器，可以将 display 属性设置为 grid 或 inline-grid。

网格容器内放置着由列和行内组成的网格元素。


### grid-template-columns 属性

grid-template-columns 属性定义了网格布局中的列的数量，它也可以设置每个列的宽度。

属性值是一个以空格分隔的列表，其中每个值定义相对应列的宽度。

如果您希望网格布局包含 4 列，则需要设置 4 列的宽度，如果所有列的宽度都是一样的，可以设置为 auto。

以下实例设置了 4 列的网格布局：


## 实例

```text
.grid-container {
  display: grid;
  grid-template-columns: auto auto auto auto;
}
```

注意：如果您在 4 列网格中有 4 个以上的网格元素，网格布局会生成新的一行放置该元素。

grid-template-columns 属性也可用于指定列的宽度。


## 实例

```text
.grid-container {
  display: grid;
  grid-template-columns: 80px 200px auto 40px;
}
```


### grid-template-rows 属性

grid-template-rows 属性设置每一行的高度。

属性值是一个以空格分隔的列表，其中每个值定义相对应行的高度：


## 实例

```text
.grid-container {
  display: grid;
  grid-template-rows: 80px 200px;
}
```


### justify-content 属性

justify-content 属性用于对齐容器内的网格，设置如何分配顺着弹性容器主轴(或者网格行轴) 的元素之间及其周围的空间。

注意：网格的总宽度必须小于容器的宽度才能使 justify-content 属性生效。

justify-content 详细内容参考：CSS justify-content 属性


## 实例

```text
.grid-container {
  display: grid;
  justify-content: space-evenly;
}
```


## 实例

```text
.grid-container {
  display: grid;
  justify-content: space-around;
}
```


## 实例

```text
.grid-container {
  display: grid;
  justify-content: space-between;
}
```


## 实例

```text
.grid-container {
  display: grid;
  justify-content: center;
}
```


## 实例

```text
.grid-container {
  display: grid;
  justify-content: start;
}
```


## 实例

```text
.grid-container {
  display: grid;
  justify-content: end;
}
```


### align-content 属性

align-content 属性用于设置垂直方向上的网格元素在容器中的对齐方式。

注意：网格元素的总高度必须小于容器的高度才能使 align-content 属性生效。


## 实例

```text
.grid-container {
  display: grid;
  height: 400px;
  align-content: center;
}
```


## 实例

```text
.grid-container {
  display: grid;
  height: 400px;
  align-content: space-evenly;
}
```


## 实例

```text
.grid-container {
  display: grid;
  height: 400px;
  align-content: space-around;
}
```


## 实例

```text
.grid-container {
  display: grid;
  height: 400px;
  align-content: space-between;
}
```


## 实例

```text
.grid-container {
  display: grid;
  height: 400px;
  align-content: start;
}
```


## 实例

```text
.grid-container {
  display: grid;
  height: 400px;
  align-content: end;
}
```


## 复习重点

- 能说明 `CSS 网格容器` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
