# jQuery Mobile：jQuery Mobile 按钮图标

- 来源：[jQuery Mobile 按钮图标](https://www.runoob.com/jquerymobile/jquerymobile-icons.html)
- 分类：移动开发
- 技术：jQuery Mobile
- 笔记类型：练习笔记
- 章节序号：3337

## 本章内容

jQuery Mobile 提供了一套让按钮看起来更称心如意的图标。


## 添加图标到 jQuery Mobile 按钮

我们可以使用 ui-icon 类将图标添加到按钮上，并可以使用指定类来设置按钮位置。

```html
<a href="#anylink" class="ui-btn ui-icon-search ui-btn-icon-left">Search</a>
```

注意： 在其他方式的按钮上，如列表或表单中的按钮需要使用 data-icon 属性。在接下来的章节中我们会具体介绍。

下面我们列出一些 jQuery Mobile 提供的可用图标：

如需查看所有 jQuery Mobile 按钮图标的完整参考手册，请访问我们的 jQuery Mobile 图标参考手册。


## 定位图标

您也可以规定图标定位在按钮的什么部位：顶部（top）、右侧（right）、底部（bottom）、左侧（left）。

请使用 ui-btn-icon 属性来指定位置：


## 图标的位置：


## 只显示图标

如果你只想显示图标，可以使用 "notext":


## 实例：


## 移除圆圈

默认情况下，所有的图标都有一个灰色的圆圈。如果你不需要它，可以在元素中使用 "ui-nodisc-icon" 类：


## 实例


## 黑色、白色按钮

默认情况下，所有图标都是白色的。 如果需要改变图标颜色为黑色，可以在元素添加 "ui-alt-icon"：


## 实例


## 更多实例

向容器添加 "ui-nodisc-icon" 类 使用 "ui-nodisc-icon" 类的实例。

向容器添加 "ui-alt-icon" 类 使用 "ui-alt-icon" 类的实例。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jQuery Mobile 按钮图标` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
