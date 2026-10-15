# jQuery Mobile：jQuery Mobile 导航栏

- 来源：[jQuery Mobile 导航栏](https://www.runoob.com/jquerymobile/jquerymobile-navbars.html)
- 分类：移动开发
- 技术：jQuery Mobile
- 笔记类型：练习笔记
- 章节序号：3340

## 本章内容

导航栏是由一组水平排列的链接组成，通常包含在头部或尾部内。

默认情况下，导航栏中的链接将自动变成按钮（不需要 data-role="button"）。

使用 data-role="navbar" 属性来定义导航栏：


## 实例


## 导航按钮图标

我们可以使用 data-icon 属性为导航按钮添加图标:


## 实例

data-icon 属性与在图标章节中的 CSS 类使用相同的值。CSS 类使用方法 class="ui-icon-value", data-icon 属性使用方法 data-icon="value"。

如需查看所有 jQuery Mobile 按钮图标的完整参考手册，请访问我们的 jQuery Mobile 图标参考手册。


## 定位图标

就像 "ui-btn-icon-position" 类一样 (图标章节有详细说明), 你可以设置图标显示的位置： top（头部）, right（右侧）, bottom（底部） 或 left（左侧）。

图标位置在导航栏容器上设置，使用 data-iconpos 属性来指定位置：


## 激活按钮

当导航栏中的某个链接被点击，它将获得被选中（按下）的外观。

如果想在不点击链接时获得这种外观，请使用 class="ui-btn-active"：


## 实例

对于多个页面，您可能想要每个按钮的选中外观代表当前用户所在的页面。要做到这一点，请添加 "ui-state-persist" 和 "ui-btn-active" 到链接的 class：


## 实例


## 更多实例

内容中的导航栏 如何在 data-role="content" 内添加导航栏。

尾部中的导航栏 如何在尾部内添加导航栏。

导航栏中的定位图标 如何在尾部内的导航栏中定位图标。

超过 5 个按钮 导航栏中 10 个按钮的演示。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jQuery Mobile 导航栏` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
