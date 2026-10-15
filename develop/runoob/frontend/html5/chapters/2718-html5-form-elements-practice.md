# HTML5：HTML5 表单元素

- 来源：[HTML5 表单元素](https://www.runoob.com/html/html5-form-elements.html)
- 分类：前端开发
- 技术：HTML5
- 笔记类型：练习笔记
- 章节序号：2718

## 本章内容

## HTML5 新的表单元素

HTML5 有以下新的表单元素:

- <datalist>
- <keygen>
- <output>

注意:不是所有的浏览器都支持HTML5 新的表单元素，但是你可以在使用它们，即使浏览器不支持表单属性，仍然可以显示为常规的表单元素。


## HTML5 <datalist> 元素

<datalist> 元素规定输入域的选项列表。

<datalist> 属性规定 form 或 input 域应该拥有自动完成功能。当用户在自动完成域中开始输入时，浏览器应该在该域中显示填写的选项：

使用 <input> 元素的列表属性与 <datalist> 元素绑定.


## 实例

<input> 元素使用<datalist>预定义值:

```html
<input list="browsers">

<datalist id="browsers">
  <option value="Internet Explorer">
  <option value="Firefox">
  <option value="Chrome">
  <option value="Opera">
  <option value="Safari">
</datalist>
```


## HTML5 <keygen> 元素

<keygen> 元素的作用是提供一种验证用户的可靠方法。

<keygen>标签规定用于表单的密钥对生成器字段。

当提交表单时，会生成两个键，一个是私钥，一个公钥。

私钥（private key）存储于客户端，公钥（public key）则被发送到服务器。公钥可用于之后验证用户的客户端证书（client certificate）。

该元素已被废弃，不再推荐使用，替代方案包括：

- 使用 Web Cryptography API 在 JavaScript 中生成密钥
- 使用专门的加密库


## 实例

带有keygen字段的表单:

```html
<form action="demo_keygen.asp" method="get">
用户名: <input type="text" name="usr_name">
加密: <keygen name="security">
<input type="submit">
</form>
```


## HTML5 <output> 元素

<output> 元素用于不同类型的输出，比如计算或脚本输出：


## 实例

将计算结果显示在 <output> 元素:

```html
<form oninput="x.value=parseInt(a.value)+parseInt(b.value)">0
<input type="range" id="a" value="50">100 +
<input type="number" id="b" value="50">=
<output name="x" for="a b"></output>
</form>
```


## HTML5 新表单元素


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `HTML5 表单元素` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
