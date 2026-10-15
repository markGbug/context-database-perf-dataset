# jQuery Mobile：jQuery Mobile 表单滑动条

- 来源：[jQuery Mobile 表单滑动条](https://www.runoob.com/jquerymobile/jquerymobile-form-sliders.html)
- 分类：移动开发
- 技术：jQuery Mobile
- 笔记类型：练习笔记
- 章节序号：3351

## 本章内容

## jQuery Mobile 滑动条控件

滑动条允许您从一个范围的数字中选择一个值：

如需创建滑动条，请使用 <input type="range">：


## 实例

使用以下属性来规定限制：

- max - 规定允许的最大值
- min - 规定允许的最小值
- step - 规定合法的数字间隔
- value - 规定默认值

提示: 如果你想在按钮中显示进度的值可以添加 data-show-value="true" 属性:


## 实例

提示: 如果你想在滑动按钮上显示进度（类似一个小弹窗）可以使用 data-popup-enabled="true" 属性:


## 实例

提示：如果您想要高亮突出显示滑动条的值，请添加 data-highlight="true"：


## 实例


## 拨动开关

拨动开关通常用于 on/off 或 true/false 按钮：

我们可以使用 <input type="checkbox"> 元素并指定 data-role 为 "flipswitch" 来创建开关:


## 实例

默认情况下，开关切换的文本为 "On" 和 "Off"。你可以使用 data-on-text 和 data-off-text 属性来修改它：


### 实例

提示:开关复选框可以使用 "checked" 属性来设置默认的选项：


## 实例


## 更多实例

区间滑块 制作一个区间值的滑块。

滑块样式 为滑块开关设置样式。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jQuery Mobile 表单滑动条` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
