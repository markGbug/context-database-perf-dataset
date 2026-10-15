# CSS：CSS !important 规则

- 来源：[CSS !important](https://www.runoob.com/css/css-important.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：学习笔记
- 章节序号：2427

## 本章内容

### 什么是 !important

CSS 中的 !important 规则用于增加样式的权重。

!important 与优先级无关，但它与最终的结果直接相关，使用一个 !important 规则时，此声明将覆盖任何其他声明。


## 实例

```text
#myid {
  background-color: blue;
}

.myclass {
  background-color: gray;
}

p {
  background-color: red !important;
}
```

以上实例中，尽管 ID 选择器和类选择器具有更高的优先级，但三个段落背景颜色都显示为红色，因为 !important 规则会覆盖 background-color 属性。


### 重要说明

使用 !important 是一个坏习惯，应该尽量避免，因为这破坏了样式表中的固有的级联规则 使得调试找 bug 变得更加困难了。

当两条相互冲突的带有 !important 规则的声明被应用到相同的元素上时，拥有更大优先级的声明将会被采用。

以下实例我们在查看 CSS 源码时就不是很清楚哪种颜色最重要：


## 实例

```text
#myid {
  background-color: blue !important;
}

.myclass {
  background-color: gray !important;
}

p {
  background-color: red !important;
}
```

使用建议：

- 一定要优先考虑使用样式规则的优先级来解决问题而不是 !important
- 只有在需要覆盖全站或外部 CSS 的特定页面中使用 !important
- 永远不要在你的插件中使用 !important
- 永远不要在全站范围的 CSS 代码中使用 !important


### 何时使用 !important

如果要在你的网站上设定一个全站样式的 CSS 样式可以使用 !important。

比如我们要让网站上所有按钮的样式都一样：


## 实例

```text
.button {
  background-color: #8c8c8c;
  color: white;
  padding: 5px;
  border: 1px solid black;
}
```

如果我们将按钮放在另一个具有更优先级的元素中，按钮的外观就会发生变化，并且属性会发生冲突，如下实例：


## 实例

```text
.button {
  background-color: #8c8c8c;
  color: white;
  padding: 5px;
  border: 1px solid black;
}

#myDiv a {
  color: red;
  background-color: yellow;
}
```

如果想要设置所有按钮具有相同的外观，我们可以将 !important 规则添加到按钮的样式属性中，如下所示：


## 实例

```text
.button {
  background-color: #8c8c8c !important;
  color: white !important;
  padding: 5px !important;
  border: 1px solid black !important;
}

#myDiv a {
  color: red;
  background-color: yellow;
}
```


## 复习重点

- 能说明 `CSS !important` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
