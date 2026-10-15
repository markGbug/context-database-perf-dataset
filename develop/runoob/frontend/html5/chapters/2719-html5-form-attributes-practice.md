# HTML5：HTML5 表单属性

- 来源：[HTML5 表单属性](https://www.runoob.com/html/html5-form-attributes.html)
- 分类：前端开发
- 技术：HTML5
- 笔记类型：练习笔记
- 章节序号：2719

## 本章内容

## HTML5 新的表单属性

HTML5 的 <form> 和 <input>标签添加了几个新属性.

<form>新属性：

- autocomplete
- novalidate

<input>新属性：

- autocomplete
- autofocus
- form
- formaction
- formenctype
- formmethod
- formnovalidate
- formtarget
- height 与 width
- list
- min 与 max
- multiple
- pattern (regexp)
- placeholder
- required
- step


## <form> / <input> autocomplete 属性

autocomplete 属性规定 form 或 input 域应该拥有自动完成功能。

当用户在自动完成域中开始输入时，浏览器应该在该域中显示填写的选项。

提示: autocomplete 属性有可能在 form元素中是开启的，而在input元素中是关闭的。

注意: autocomplete 适用于 <form> 标签，以及以下类型的 <input> 标签：text, search, url, telephone, email, password, datepickers, range 以及 color。


## 实例

HTML form 中开启 autocomplete (一个 input 字段关闭 autocomplete ):

```html
<form action="demo-form.php" autocomplete="on">
  First name:<input type="text" name="fname"><br>
  Last name: <input type="text" name="lname"><br>
  E-mail: <input type="email" name="email" autocomplete="off"><br>
  <input type="submit">
</form>
```

提示:某些浏览器中，您可能需要启用自动完成功能，以使该属性生效。


## <form> novalidate 属性

novalidate 是一个布尔（true 或 false）属性。

novalidate 属性是 HTML 表单元素的一个布尔属性，用于设置浏览器不对表单进行验证。

当该属性被添加到 <form> 元素上时，浏览器将不会执行默认的表单验证，不会检查输入字段是否符合指定的验证规则。

使用 novalidate 属性可以让开发者完全控制表单验证的逻辑，可以通过 JavaScript 或其他方式来自定义表单验证的行为。


## 实例

无需验证提交的表单数据

```html
<form action="demo-form.php" novalidate>
  E-mail: <input type="email" name="user_email">
  <input type="submit">
</form>
```


## <input> autofocus 属性

autofocus 属性是一个布尔属性。

autofocus 属性规定在页面加载时，域自动地获得焦点。


## 实例

让 "First name" input 输入域在页面载入时自动聚焦：

```html
First name:<input type="text" name="fname" autofocus>
```


## <input> form 属性

form 属性规定输入域所属的一个或多个表单。

提示:如需引用一个以上的表单，请使用空格分隔的列表。


## 实例

位于form表单外的 input 字段引用了 HTML form (该 input 表单仍然属于form表单的一部分):

```html
<form action="demo-form.php" id="form1">
  First name: <input type="text" name="fname"><br>
  <input type="submit" value="提交">
</form>

Last name: <input type="text" name="lname" form="form1">
```


## <input> formaction 属性

The formaction 属性用于描述表单提交的URL地址.

The formaction 属性会覆盖<form> 元素中的action属性.

注意: The formaction 属性用于 type="submit" 和 type="image".


## 实例

以下HTMLform表单包含了两个不同地址的提交按钮：

```html
<form action="demo-form.php">
  First name: <input type="text" name="fname"><br>
  Last name: <input type="text" name="lname"><br>
  <input type="submit" value="提交"><br>
  <input type="submit" formaction="demo-admin.php"
  value="提交">
</form>
```


## <input> formenctype 属性

formenctype 属性描述了表单提交到服务器的数据编码 (只对form表单中 method="post" 表单)

formenctype 属性覆盖 form 元素的 enctype 属性。

主要: 该属性与 type="submit" 和 type="image" 配合使用。


## 实例

第一个提交按钮以默认编码发送表单数据，第二个提交按钮以 "multipart/form-data" 编码格式发送表单数据:

```html
<form action="demo-post_enctype.php" method="post">
  First name: <input type="text" name="fname"><br>
  <input type="submit" value="提交">
  <input type="submit" formenctype="multipart/form-data"
  value="以 Multipart/form-data 提交">
</form>
```


## <input> formmethod 属性

formmethod 属性定义了表单提交的方式。

formmethod 属性覆盖了 <form> 元素的 method 属性。

注意: 该属性可以与 type="submit" 和 type="image" 配合使用。


## 实例

重新定义表单提交方式实例:

```html
<form action="demo-form.php" method="get">
  First name: <input type="text" name="fname"><br>
  Last name: <input type="text" name="lname"><br>
  <input type="submit" value="提交">
  <input type="submit" formmethod="post" formaction="demo-post.php"
  value="使用 POST 提交">
</form>
```


## <input> formnovalidate 属性

novalidate 属性是一个 boolean 属性.

novalidate属性描述了 <input> 元素在表单提交时无需被验证。

formnovalidate 属性会覆盖 <form> 元素的novalidate属性.


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `HTML5 表单属性` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
