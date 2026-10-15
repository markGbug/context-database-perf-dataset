# CSS：CSS 计数器

- 来源：[CSS 计数器](https://www.runoob.com/css/css-counters.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：练习笔记
- 章节序号：2425

## 本章内容

CSS 计数器通过一个变量来设置，根据规则递增变量。


## 使用计数器自动编号

CSS 计数器根据规则来递增变量。

CSS 计数器使用到以下几个属性：

- counter-reset - 创建或者重置计数器
- counter-increment - 递增变量
- content - 插入生成的内容
- counter() 或 counters() 函数 - 将计数器的值添加到元素

要使用 CSS 计数器，得先用 counter-reset 创建：

以下实例在页面创建一个计数器 (在 body 选择器中)，每个 <h2> 元素的计数值都会递增，并在每个 <h2> 元素前添加 "Section <计数值>:"


## CSS 实例

```text
body {
  counter-reset: section;
}

h2::before {
  counter-increment: section;
  content: "Section " counter(section) ": ";
}
```


## 嵌套计数器

以下实例在页面创建一个计数器，在每一个 <h1> 元素前添加计数值 "Section <主标题计数值>.", 嵌套的计数值则放在 <h2> 元素的前面，内容为 "<主标题计数值>.<副标题计数值>":


## CSS 实例

```text
body {
  counter-reset: section;
}

h1 {
  counter-reset: subsection;
}

h1::before {
  counter-increment: section;
  content: "Section " counter(section) ". ";
}

h2::before {
  counter-increment: subsection;
  content: counter(section) "." counter(subsection) " ";
}
```

计数器也可用于列表中，列表的子元素会自动创建。这里我们使用了 counters() 函数在不同的嵌套层级中插入字符串:


## CSS 实例

```text
ol {
  counter-reset: section;
  list-style-type: none;
}

li::before {
  counter-increment: section;
  content: counters(section,".") " ";
}
```


## CSS 计数器属性


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CSS 计数器` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
