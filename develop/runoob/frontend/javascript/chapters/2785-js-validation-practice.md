# JavaScript：JavaScript 表单

- 来源：[JavaScript 表单](https://www.runoob.com/js/js-validation.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：练习笔记
- 章节序号：2785

## 本章内容

## JavaScript 表单验证

HTML 表单验证可以通过 JavaScript 来完成。

以下实例代码用于判断表单字段(fname)值是否存在， 如果不存在，就弹出信息，阻止表单提交：


## JavaScript 实例

```javascript
function validateForm() {
    var x = document.forms["myForm"]["fname"].value;
    if (x == null || x == "") {
        alert("需要输入名字。");
        return false;
    }
}
```

以上 JavaScript 代码可以通过 HTML 代码来调用：


## HTML 表单实例

```html
<form name="myForm" action="demo_form.php" onsubmit="return validateForm()" method="post">
名字: <input type="text" name="fname">
<input type="submit" value="提交">
</form>
```


## JavaScript 验证输入的数字

JavaScript 常用于对输入数字的验证：

请输入 1 到 10 之间的数字：


## HTML 表单自动验证

HTML 表单验证也可以通过浏览器来自动完成。

如果表单字段 (fname) 的值为空, required 属性会阻止表单提交：


## 实例

```html
<form action="demo_form.php" method="post">
  <input type="text" name="fname" required="required">
  <input type="submit" value="提交">
</form>
```

Internet Explorer 9 及更早 IE 浏览器不支持表单自动验证。


## 数据验证

数据验证用于确保用户输入的数据是有效的。

典型的数据验证有：

- 必需字段是否有输入?
- 用户是否输入了合法的数据?
- 在数字字段是否输入了文本?

大多数情况下，数据验证用于确保用户正确输入数据。

数据验证可以使用不同方法来定义，并通过多种方式来调用。

服务端数据验证是在数据提交到服务器上后再验证。

客户端数据验证是在数据发送到服务器前，在浏览器上完成验证。


## HTML 约束验证

HTML5 新增了 HTML 表单的验证方式：约束验证（constraint validation）。

约束验证是表单被提交时浏览器用来实现验证的一种算法。

HTML 约束验证基于：

- HTML 输入属性
- CSS 伪类选择器
- DOM 属性和方法


### 约束验证 HTML 输入属性

完整列表，请查看 HTML 输入属性。


### 约束验证 CSS 伪类选择器

完整列表，请查看 CSS 伪类。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `JavaScript 表单` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
