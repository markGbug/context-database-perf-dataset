# JavaScript：JavaScript 表单验证

- 来源：[JavaScript 表单验证](https://www.runoob.com/js/js-form-validation.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：学习笔记
- 章节序号：2786

## 本章内容

表单验证是确保用户输入的数据符合预期格式和规则的过程。

在 Web 开发中，表单验证通常用于检查用户输入的有效性，例如电子邮件地址、密码、电话号码等。

通过表单验证，可以防止无效数据提交到服务器，从而提高数据的准确性和安全性。


## JavaScript 表单验证

JavaScript 可用来在数据被送往服务器前对 HTML 表单中的这些输入数据进行验证。

表单数据经常需要使用 JavaScript 来验证其正确性：

- 验证表单数据是否为空？
- 验证输入是否是一个正确的email地址？
- 验证日期是否输入正确？
- 验证表单输入内容是否为数字型？


### 为什么需要表单验证？

- 数据准确性：确保用户输入的数据符合预期格式，避免无效数据。
- 安全性：防止恶意用户提交有害数据，如 SQL 注入、跨站脚本攻击（XSS）等。
- 用户体验：及时反馈用户输入错误，帮助用户快速纠正问题。


## JavaScript 表单验证的基本方法

JavaScript 提供了多种方法来实现表单验证。以下是几种常见的方式：


### 1. 使用 HTML5 内置验证

HTML5 提供了一些内置的表单验证功能，例如 required、pattern、min、max 等属性。这些属性可以简单地实现基本的表单验证。


## 实例

在上面的例子中，required 属性确保用户必须输入电子邮件地址，而 type="email" 会自动验证输入是否为有效的电子邮件格式。


### 2. 使用 JavaScript 自定义验证

下面的函数用来检查用户是否已填写表单中的必填（或必选）项目。假如必填或必选项为空，那么警告框会弹出，并且函数的返回值为 false，否则函数的返回值则为 true（意味着数据没有问题）：

```javascript
function validateForm()
{
  var x=document.forms["myForm"]["fname"].value;
  if (x==null || x=="")
  {
    alert("姓必须填写");
    return false;
  }
}
```

以上函数在 form 表单提交时被调用:


## 实例

```html
<form name="myForm" action="demo-form.php" onsubmit="return validateForm()" method="post">
姓: <input type="text" name="fname">
<input type="submit" value="提交">
</form>
```


## E-mail 验证

下面的函数检查输入的数据是否符合电子邮件地址的基本语法。

意思就是说，输入的数据必须包含 @ 符号和点号(.)。同时，@ 不可以是邮件地址的首字符，并且 @ 之后需有至少一个点号：

```html
function validateForm(){
  var x=document.forms["myForm"]["email"].value;
  var atpos=x.indexOf("@");
  var dotpos=x.lastIndexOf(".");
  if (atpos<1 || dotpos<atpos+2 || dotpos+2>=x.length){
    alert("不是一个有效的 e-mail 地址");
    return false;
  }
}
```

下面是连同 HTML 表单的完整代码：


## 实例

```html
<form name="myForm" action="demo-form.php" onsubmit="return validateForm();" method="post">
    Email: <input type="text" name="email">
    <input type="submit" value="提交">
</form>
```


### 使用正则表达式进行验证

正则表达式（Regular Expression）是一种强大的工具，可以用于匹配复杂的字符串模式。

以下是一个使用正则表达式验证电子邮件地址的例子：


## 实例

在这个例子中，我们定义了一个正则表达式来验证电子邮件地址的格式。如果输入的电子邮件地址符合格式要求，函数会返回 true，否则返回 false。


## 复习重点

- 能说明 `JavaScript 表单验证` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
