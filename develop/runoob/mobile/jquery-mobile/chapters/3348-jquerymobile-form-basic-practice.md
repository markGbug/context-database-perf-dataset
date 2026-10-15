# jQuery Mobile：jQuery Mobile 表单

- 来源：[jQuery Mobile 表单基础](https://www.runoob.com/jquerymobile/jquerymobile-form-basic.html)
- 分类：移动开发
- 技术：jQuery Mobile
- 笔记类型：练习笔记
- 章节序号：3348

## 本章内容

jQuery Mobile 会自动为 HTML 表单自动添加样式，让它们看起来更具吸引力，触摸起来更具友好性。


## jQuery Mobile 表单结构

jQuery Mobile 使用 CSS 为 HTML 表单元素添加样式，让它们更具吸引力，更易于使用。

在 jQuery Mobile 中，您可以使用下列表单控件：

- 文本输入框
- 搜索输入框
- 单选按钮
- 复选框
- 选择菜单
- 滑动条
- 翻转拨动开关

当使用 jQuery Mobile 表单时，您应当知道：

- <form> 元素必须有一个 method 和一个 action 属性
- 每个表单元素必须有一个唯一的 "id" 属性。id 必须是整个站点所有页面上唯一的。这是因为 jQuery Mobile 的单页导航机制使得多个不同页面在同一时间被呈现
- 每个表单元素必须有一个标签。设置标签的 for 属性来匹配元素的 id


## 实例

如需隐藏标签，请使用 class ui-hidden-accessible。这在您把元素的 placeholder 属性作为标签时经常用到：


## 实例

提示： 我们可以使用 data-clear-btn="true" 属性来添加清除输入框内容的按钮 (一个在输入框右侧的 X 图标):


## 实例


## jQuery Mobile 表单图标

表单中的按钮代码是标准的 HTML <input> 元素 (button, reset, submit)。他们会自动渲染样式，可以自动适配移动设备与桌面设备：


## 实例

如果需要在 <input> 按钮中添加额外的样式，可以使用下表中的 data-* 属性：


## 按钮添加图标：


## 字段容器

如需让标签和表单元素看起来更适应宽屏，请用带有 "ui-field-contain" 类的 <div> 或 <fieldset> 元素包围 label/form 元素：


## 实例

提示：为了防止 jQuery Mobile 为可点击元素自动添加样式，请使用 data-role="none" 属性：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jQuery Mobile 表单基础` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
