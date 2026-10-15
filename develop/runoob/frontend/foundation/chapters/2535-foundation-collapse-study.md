# Foundation：Foundation 折叠列表

- 来源：[Foundation 折叠列表](https://www.runoob.com/foundation/foundation-collapse.html)
- 分类：前端开发
- 技术：Foundation
- 笔记类型：学习笔记
- 章节序号：2535

## 本章内容

在你想隐藏部分内容的显示时，可以使用折叠列表。


### 实例


### 实例解析

.accordion 类和 data-accordion 属性用于创建一个可折叠的元素。 .accordion-navigation 类用于渲染可折叠元素。实际的内容在 .content 类 (<div class="content") 中，点击按钮既可以显示。

我们在列表项中添加 <a> 元素来控制（显示/隐藏）可折叠的内容。然后锚链接使用与可折叠内容内容相同的id (<a href=#demo" 与 <div id="demo"> 相关联)。

注意： 可折叠的效果需要初始化 Foundation JS。

默认情况下，可折叠内容是隐藏的。我们可以通过在 <div> 上添加 .active 类让其默认是显示的：


### 实例


## 手风琴效果

手风琴效果用于延展与设置可折叠内容。

手风琴效果通过使用多个不同的锚链接与id来创建：


### 实例

默认情况下，手风琴列表项有一个是打开的。如果你想关闭所有可以使用 data-options="multi_expand:true;" 属性:


### 实例


## 复习重点

- 能说明 `Foundation 折叠列表` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
