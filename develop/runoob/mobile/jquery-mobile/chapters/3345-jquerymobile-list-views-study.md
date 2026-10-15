# jQuery Mobile：jQuery Mobile 列表视图

- 来源：[jQuery Mobile 列表视图](https://www.runoob.com/jquerymobile/jquerymobile-list-views.html)
- 分类：移动开发
- 技术：jQuery Mobile
- 笔记类型：学习笔记
- 章节序号：3345

## 本章内容

## jQuery Mobile 列表视图

jQuery Mobile 中的列表视图是标准的HTML 列表; 有序(<ol>) 和 无序(<ul>).

列表视图是jQuery Mobile中功能强大的一个特性。它会使标准的无序或有序列表应用更广泛。应用方法就是在ul或ol标签中添加data-role="listview"属性。在每个项目(<li>)中添加链接，用户可以点击它：


## 实例

列表样式的圆角和边缘，使用 data-inset="true" 属性设置:


## 实例


## 列表分隔

列表项也可以转化为列表分割项，用来组织列表，使列表项成组。

指定列表分割，给列表项<li>元素添加 data-role="list-divider" 属性即可：


## 实例

如果你有一个字母顺序排列的列表，（例如一个电话簿）通过 <ol> 或者<ul> 元素的 data-autodividers="true" 属性设置可以配置为自动生成的项目的分隔:


## 实例


## 更多实例

只读列表 如何创建一个不带链接的列表 (不会是个按钮且不可点击)。

面板 如何在列表中插入面板


## 复习重点

- 能说明 `jQuery Mobile 列表视图` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
