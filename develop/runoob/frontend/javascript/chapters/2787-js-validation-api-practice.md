# JavaScript：JavaScript 验证 API

- 来源：[JavaScript 验证 API](https://www.runoob.com/js/js-validation-api.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：练习笔记
- 章节序号：2787

## 本章内容

## 约束验证 DOM 方法

设置 input 元素的 validationMessage 属性，用于自定义错误提示信息的方法。

使用 setCustomValidity 设置了自定义提示后，validity.customError 就会变成 true，checkValidity 总是会返回 false。如果要重新判断需要取消自定义提示，方式如下：

```text
setCustomValidity('')
setCustomValidity(null)
setCustomValidity(undefined)
```

以下实例如果输入信息不合法，则返回错误信息：


## checkValidity() 方法

```html
<input id="id1" type="number" min="100" max="300" required>
<button onclick="myFunction()">验证</button>

<p id="demo"></p>

<script>
```

```javascript
function myFunction() {
    var inpObj = document.getElementById("id1");
    if (inpObj.checkValidity() == false) {
        document.getElementById("demo").innerHTML = inpObj.validationMessage;
    }
}
```

```text
</script>
```


## 约束验证 DOM 属性


## Validity 属性

input 元素的 validity 属性包含一系列关于 validity 数据属性:


## 实例

如果输入的值大于 100，显示一个信息：


## rangeOverflow 属性

```html
<input id="id1" type="number" max="100">
<button onclick="myFunction()">验证</button>

<p id="demo"></p>

<script>
```

```javascript
function myFunction() {
    var txt = "";
    if (document.getElementById("id1").validity.rangeOverflow) {
       txt = "输入的值太大了";
    }
    document.getElementById("demo").innerHTML = txt;
}
```

```text
</script>
```

如果输入的值小于 100，显示一个信息：


## rangeUnderflow 属性

```html
<input id="id1" type="number" min="100" required>
<button onclick="myFunction()">OK</button>

<p id="demo"></p>

<script>
```

```javascript
function myFunction() {
    var txt = "";
    var inpObj = document.getElementById("id1");
    if(!isNumeric(inpObj.value)) {
        txt = "你输入的不是数字";
    } else if (inpObj.validity.rangeUnderflow) {
        txt = "输入的值太小了";
    } else {
        txt = "输入正确";
    }
    document.getElementById("demo").innerHTML = txt;
}

// 判断输入是否为数字
function isNumeric(n) {
    return !isNaN(parseFloat(n)) && isFinite(n);
}
```

```text
</script>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `JavaScript 验证 API` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
