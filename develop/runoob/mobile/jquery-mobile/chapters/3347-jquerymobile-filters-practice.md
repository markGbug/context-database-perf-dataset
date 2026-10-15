# jQuery Mobile：jQuery Mobile 过滤

- 来源：[jQuery Mobile 过滤](https://www.runoob.com/jquerymobile/jquerymobile-filters.html)
- 分类：移动开发
- 技术：jQuery Mobile
- 笔记类型：练习笔记
- 章节序号：3347

## 本章内容

## 可过滤元素

所有的元素如果有一个或更多的子元素均可过滤。

如何创建搜索字段:

- 你想过滤的元素必须使用 data-filter="true" 属性。
- 创建 <input> 元素并指定 id，元素上加上 data-type="search" 属性。这样就能创建基本的搜索字段。将 <input> 元素放置于一个表单中，表单 <form> 元素使用 "ui-filterable" 类 - 该类会调整搜索字段与过滤元素的外边距。
- 接着为过滤的元素添加 data-input 属性。该值需要是 <input> 元素的 id。

接下来我们创建一个可过滤的列表：


## 列表中搜索元素

提示: 可以在搜索字段中使用 placeholder 属性来设置提示信息：


## 实例


## 自定义过滤

一般的插入到各个列表项的文本就是作为过滤的文本使用(如 A 对应 "Adele" 或 "B" 对应 "Billy")。 但是，如果你想指定自定义的过滤的文本，你需要在子元素中使用 data-filtertext 属性:


### 实例


## 更多实例

过滤折叠列表 如何过滤折叠的列表。

过滤表格 如何过滤表格内容。

过滤 <div> 元素 如何过滤 <div> 元素中包含的子 <p> 元素。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jQuery Mobile 过滤` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
