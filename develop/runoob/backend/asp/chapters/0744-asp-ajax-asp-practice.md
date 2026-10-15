# ASP：ASP - AJAX 与 ASP

- 来源：[AJAX ASP](https://www.runoob.com/asp/asp-ajax-asp.html)
- 分类：后端开发
- 技术：ASP
- 笔记类型：练习笔记
- 章节序号：0744

## 本章内容

AJAX 被用于创建交互性更强的应用程序。


## AJAX ASP 实例

下面的实例将演示当用户在输入框中键入字符时，网页如何与 Web 服务器进行通信：


## 实例

Start typing a name in the input field below:

Suggestions:


## 实例解释 - HTML 页面

当用户在上面的输入框中键入字符时，会执行 "showHint()" 函数。该函数由 "onkeyup" 事件触发：

源代码解释：

如果输入框是空的（str.length==0），该函数会清空 txtHint 占位符的内容，并退出该函数。

如果输入框不是空的，那么 showHint() 会执行以下步骤：

- 创建 XMLHttpRequest 对象
- 创建在服务器响应就绪时执行的函数
- 向服务器上的文件发送请求
- 请注意添加到 URL 末端的参数（q）（包含输入框的内容）


## ASP 文件

上面这段通过 JavaScript 调用的服务器页面是名为 "gethint.asp" 的 ASP 文件。

"gethint.asp" 中的源代码会检查姓名数组，然后向浏览器返回对应的姓名：

解释：如果 JavaScript 发送了任何文本（即 strlen($q) > 0），则会发生：

- 查找匹配 JavaScript 发送的字符的姓名
- 如果未找到匹配，则将响应字符串设置为 "no suggestion"
- 如果找到一个或多个匹配姓名，则用所有姓名设置响应字符串
- 把响应发送到 "txtHint" 占位符


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `AJAX ASP` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
