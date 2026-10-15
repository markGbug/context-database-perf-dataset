# JavaScript：JavaScript 错误 - throw、try 和 catch

- 来源：[JavaScript 错误](https://www.runoob.com/js/js-errors.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：练习笔记
- 章节序号：2780

## 本章内容

try 语句测试代码块的错误。

catch 语句处理错误。

throw 语句创建自定义错误。

finally 语句在 try 和 catch 语句之后，无论是否有触发异常，该语句都会执行。


## JavaScript 错误

当 JavaScript 引擎执行 JavaScript 代码时，会发生各种错误。

可能是语法错误，通常是程序员造成的编码错误或错别字。

可能是拼写错误或语言中缺少的功能（可能由于浏览器差异）。

可能是由于来自服务器或用户的错误输出而导致的错误。

当然，也可能是由于许多其他不可预知的因素。


## JavaScript 抛出（throw）错误

当错误发生时，当事情出问题时，JavaScript 引擎通常会停止，并生成一个错误消息。

描述这种情况的技术术语是：JavaScript 将抛出一个错误。


## JavaScript try 和 catch

try 语句允许我们定义在执行时进行错误测试的代码块。

catch 语句允许我们定义当 try 代码块发生错误时，所执行的代码块。

JavaScript 语句 try 和 catch 是成对出现的。


### 语法

```text
try {
    ...    //异常的抛出
} catch(e) {
    ...    //异常的捕获与处理
} finally {
    ...    //结束处理
}
```


## 实例

在下面的例子中，我们故意在 try 块的代码中写了一个错字。

catch 块会捕捉到 try 块中的错误，并执行代码来处理它。


## 实例

```javascript
var txt="";
function message()
{
    try {
        adddlert("Welcome guest!");
    } catch(err) {
        txt="本页有一个错误。\n\n";
        txt+="错误描述：" + err.message + "\n\n";
        txt+="点击确定继续。\n\n";
        alert(txt);
    }
}
```


### finally 语句

finally 语句不论之前的 try 和 catch 中是否产生异常都会执行该代码块。


## 实例

```javascript
function myFunction() {
  // 获取元素
  const messageElement = document.getElementById("p01");
  const inputElement = document.getElementById("demo");

  // 清空之前的消息
  messageElement.innerHTML = "";

  // 获取输入值并去除首尾空格
  const rawValue = inputElement.value.trim();

  try {
    // 1. 检查是否为空
    if (rawValue === "") {
      throw new Error("输入不能为空，请填写一个数字");
    }

    // 2. 检查是否为有效数字
    if (isNaN(rawValue)) {
      throw new Error("请输入有效的数字（如：5、10.5、-3）");
    }

    // 转换为数字
    const x = Number(rawValue);

    // 3. 检查是否为整数（可根据需求调整）
    if (!Number.isInteger(x)) {
      throw new Error("请输入整数（不支持小数）");
    }

    // 4. 检查数字范围（可根据需求调整）
    if (x > 10) {
      throw new Error(`数字 ${x} 太大了，请输入 5-10 之间的数字`);
    }

    if (x < 5) {
      throw new Error(`数字 ${x} 太小了，请输入 5-10 之间的数字`);
    }

    // 5. 检查是否为负数的特殊情况
    if (x < 0) {
      throw new Error("请输入正数（不支持负数）");
    }

    // 所有验证通过
    messageElement.innerHTML = `验证通过！您输入的数字是：${x}`;
    messageElement.style.color = "green";

    // 成功时可执行其他操作
    console.log(`用户输入了有效数字：${x}`);

  } catch (err) {
    // 显示错误信息
    messageElement.innerHTML = `错误：${err.message}`;
    messageElement.style.color = "red";

    // 可选：将错误记录到控制台
    console.error("输入验证失败：", err.message);

  } finally {
    // 无论成功或失败，都清空输入框
    inputElement.value = "";

    // 可选：重新聚焦到输入框，方便用户重新输入
    inputElement.focus();
  }
}
```


## Throw 语句

throw 语句允许我们创建自定义错误。

正确的技术术语是：创建或抛出异常（exception）。

如果把 throw 与 try 和 catch 一起使用，那么您能够控制程序流，并生成自定义的错误消息。


### 语法

异常可以是 JavaScript 字符串、数字、逻辑值或对象。


## 实例

本例检测输入变量的值。如果值是错误的，会抛出一个异常（错误）。catch 会捕捉到这个错误，并显示一段自定义的错误消息：


## 实例

```javascript
function myFunction() {
    var message, x;
    message = document.getElementById("message");
    message.innerHTML = "";
    x = document.getElementById("demo").value;
    try {
        if(x == "")  throw "值为空";
        if(isNaN(x)) throw "不是数字";
        x = Number(x);
        if(x < 5)    throw "太小";
        if(x > 10)   throw "太大";
    }
    catch(err) {
        message.innerHTML = "错误: " + err;
    }
}
```

请注意，如果 getElementById 函数出错，上面的例子也会抛出一个错误。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `JavaScript 错误` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
