# jQuery Mobile：jQuery Mobile 表单输入元素

- 来源：[jQuery Mobile 表单输入](https://www.runoob.com/jquerymobile/jquerymobile-form-inputs.html)
- 分类：移动开发
- 技术：jQuery Mobile
- 笔记类型：学习笔记
- 章节序号：3349

## 本章内容

## jQuery Mobile 文本输入框

输入字段是通过标准的 HTML 元素编码的，jQuery Mobile 将为它们添加样式使其看起来更具吸引力，在移动设备上更易使用。您也能使用新的 HTML5 的 <input> 类型：


## 实例

提示：请使用 placeholder 来指定一个简短的描述，用来描述输入字段的期望值：

```html
<input placeholder="sometext">
```


## 文本域

对于多行文本输入可使用 <textarea> 。

注意：当您键入一些文本时，文本域会自动调整大小以适应新增加的行。


## 实例


## 搜索输入框

type="search" 类型的输入框是在 HTML5 中新增的，它是为输入搜索定义文本字段：


## 实例


## 单选按钮

当用户在有限数量的选择中仅选取一个选项时，使用单选按钮。

为了创建一系列单选按钮，请添加带有 type="radio" 的 input 以及相应的 label。把单选按钮包围在 <fieldset> 元素内。您也可以添加一个 <legend> 元素来定义 <fieldset> 的标题。

提示：请使用 data-role="controlgroup" 来把按钮组合在一起：


## 实例


## 复选框

当用户在有限数量的选择中选取一个或多个选项时，使用复选框：


## 实例


## 更多实例

如需水平组合单选按钮或复选框，请使用 data-type="horizontal"：


## 实例

您也可以用一个 field 容器包围 <fieldset>：


## 实例

如果您想要您的按钮中的一个预先选中，请使用 HTML 中 <input> 的 checked 属性：


## 实例

你可以将表单放在弹窗中：


## 实例


## 复习重点

- 能说明 `jQuery Mobile 表单输入` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
