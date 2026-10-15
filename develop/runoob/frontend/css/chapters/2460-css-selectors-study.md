# CSS：CSS 选择器

- 来源：[CSS 选择器](https://www.runoob.com/cssref/css-selectors.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：学习笔记
- 章节序号：2460

## 本章内容

CSS（层叠样式表）提供了多种选择器，用于选择要应用样式的 HTML 元素。

CSS 选择器用于选择你想要的元素的样式的模式。

下列表格中的 "CSS" 列表示在 CSS 版本的属性定义，CSS1、CSS2 和 CSS3 是层叠样式表（Cascading Style Sheets）的不同版本，每个版本引入了新的特性和功能，以改进网页样式的控制和设计。


### 常见的 CSS 选择器

下是一些常见的 CSS 选择器：

元素选择器（Element Selector）：通过元素名称选择 HTML 元素。

如下代码，p 选择器将选择所有 <p> 元素:

```text
p {
  color: blue;
}
```

类选择器（Class Selector）：通过类别名称选择具有特定类别的 HTML 元素。

类选择器以 . 开头，后面跟着类别名称。

如下代码，.highlight 选择器将选择所有具有类别为 "highlight" 的元素。

```text
.highlight {
  background-color: yellow;
}
```

ID 选择器（ID Selector）：通过元素的唯一标识符（ID）选择 HTML 元素。

ID 选择器以 # 开头，后面跟着 ID 名称。

如下代码，#runoob 选择器将选择具有 ID 为 "runoob" 的元素。

```text
#runoob {
  width: 200px;
}
```

属性选择器（Attribute Selector）：通过元素的属性选择 HTML 元素。属性选择器可以根据属性名和属性值进行选择。

如下代码，input[type="text"] 选择器将选择所有 type 属性为 "text" 的 <input> 元素。

```text
input[type="text"] {
  border: 1px solid gray;
}
```

后代选择器（Descendant Selector）：通过指定元素的后代关系选择 HTML 元素。

后代选择器使用空格分隔元素名称。

如下代码，div p 选择器将选择所有在 <div> 元素内的 <p> 元素。

```text
div p {
  font-weight: bold;
}
```

更多选择器参考下列表格：


## 复习重点

- 能说明 `CSS 选择器` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
