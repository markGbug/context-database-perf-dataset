# Foundation：Foundation 下拉菜单

- 来源：[Foundation 下拉菜单](https://www.runoob.com/foundation/foundation-dropdowns.html)
- 分类：前端开发
- 技术：Foundation
- 笔记类型：练习笔记
- 章节序号：2534

## 本章内容

Foundation 下拉菜单允许用户从预定义的下拉列表中选取一个值：


### 实例


### 实例解析

.dropdown 类为按钮添加一个向下的箭头符号"图标。

使用按钮或链接的 data-dropdown="id" 属性来打开下拉菜单。

id 值需要与下拉菜单的内容 (id01) 匹配。

在 <div>, <nav>, <ul> 中添加 .f-dropdown 类和 data-dropdown-content 属性来创建下拉菜单的内容。

最后初始化 Foundation JS。

注意: 在小屏幕上，所有的下拉菜单的宽度是100%。


## 下拉菜单尺寸

使用 .tiny, .small, .medium, .large 或 .mega 来修改下拉菜单的宽度。

注意: 在小屏幕上，所有的下拉菜单的宽度是100%。


### 实例


## 下拉菜单边距

可以使用 .content 类为下拉菜单添加内边距：


### 实例


## 其他实例

<div> 下拉菜单中添加多媒体元素：


### 实例


## 下拉菜单方向

默认情况下下拉菜单在底部，可以通过添加 data-options="align:left|right|top" 来修改其方向：


### 实例


## 下拉菜单触发条件

默认情况下，下拉菜单在点击按钮后显示。如果你需要在鼠标移动上去后显示，可以在按钮上使用 data-options="is_hover:true" 属性:


### 实例


## 分割按钮

我们可以在按钮上添加 .split 类来设置一个分割效果的按钮，分割后会在 <span> 元素上生成一个方向向下的图标按钮:


### 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Foundation 下拉菜单` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
