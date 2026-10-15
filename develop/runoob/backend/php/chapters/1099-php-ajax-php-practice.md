# PHP：PHP - AJAX 与 PHP

- 来源：[AJAX PHP](https://www.runoob.com/php/php-ajax-php.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：练习笔记
- 章节序号：1099

## 本章内容

AJAX (Asynchronous JavaScript and XML) 是一种用于在不刷新整个页面的情况下，与服务器交换数据的技术。

AJAX 是一种在无需重新加载整个页面的情况下，能够更新部分网页的技术，它通过在后台与服务器交换数据，并能够更新部分网页内容。

AJAX 允许网页动态更新部分内容，提供更快的用户体验。

AJAX 通常使用 XMLHttpRequest 对象在后台与服务器进行通信，尽管它也可以使用 fetch API 等现代方法。

更多内容可以参考：AJAX 教程


### AJAX 的工作原理

- 发送请求：用户通过某种方式（如点击按钮）触发 AJAX 请求。
- 创建请求：JavaScript 创建一个 XMLHttpRequest 对象，用于与服务器进行通信。
- 发送请求：通过 XMLHttpRequest 对象发送请求到服务器。
- 服务器处理：服务器接收到请求后，进行数据处理。
- 返回响应：服务器将处理结果返回给客户端。
- 更新页面：JavaScript 接收到服务器的响应后，更新网页的相应部分。


### PHP 中使用 AJAX 的步骤

1、前端：JavaScript 发起 AJAX 请求。

使用 XMLHttpRequest 或 fetch 向 PHP 服务器发送请求。

2、后端：PHP 接收并处理请求。

PHP 获取 AJAX 请求的数据，并返回结果。

3、前端：处理 PHP 返回的数据。

使用 JavaScript 解析和显示从 PHP 接收到的响应数据。


### 在 PHP 中使用 AJAX

1、创建 HTML 和 JavaScript：首先，你需要一个HTML页面和JavaScript代码来发送AJAX请求。


## 实例

2、编写PHP脚本：在服务器端，你需要一个PHP文件来处理请求并返回数据。


## 实例

3、发送请求：当用户点击按钮时，JavaScript 函数 sendRequest 会被调用，它创建一个 XMLHttpRequest 对象并发送请求到服务器。

4、处理响应：服务器处理请求后，将结果返回给客户端。客户端的 JavaScript 代码会检查响应状态，并在状态为 200（即请求成功）时更新页面内容。


## AJAX PHP 实例

下面的实例将演示当用户在输入框中键入字符时，网页如何与 Web 服务器进行通信：


## 实例

尝试在输入框中输入一个名字，如：Anna:

返回值:


## 实例解释 - HTML 页面

当用户在上面的输入框中键入字符时，会执行 "showHint()" 函数。该函数由 "onkeyup" 事件触发：


## 实例

源代码解释：

如果输入框是空的（str.length==0），该函数会清空 txtHint 占位符的内容，并退出该函数。

如果输入框不是空的，那么 showHint() 会执行以下步骤：

- 创建 XMLHttpRequest 对象
- 创建在服务器响应就绪时执行的函数
- 向服务器上的文件发送请求
- 请注意添加到 URL 末端的参数（q）（包含输入框的内容）

上面这段通过 JavaScript 调用的服务器页面是名为 "gethint.php" 的 PHP 文件。

"gethint.php" 中的源代码会检查姓名数组，然后向浏览器返回对应的姓名：


## 实例

解释：如果 JavaScript 发送了任何文本（即 strlen($q) > 0），则会发生：

- 查找匹配 JavaScript 发送的字符的姓名
- 如果未找到匹配，则将响应字符串设置为 "no suggestion"
- 如果找到一个或多个匹配姓名，则用所有姓名设置响应字符串
- 把响应发送到 "txtHint" 占位符


### 使用 fetch 和 PHP 实现 AJAX

HTML + JavaScript:


## 实例

PHP 服务器 (server.php):


## 实例

说明：

- 前端：当用户点击按钮时，JavaScript 使用 fetch() 发送一个 POST 请求到 server.php，并发送了一段 JSON 数据。
- 后端：PHP 服务器读取客户端发送的请求，处理后返回一个 JSON 响应。
- 响应处理：JavaScript 接收到 PHP 服务器的响应后，更新页面内容。


### PHP Ajax 跨域问题解决方案

如果你的异步请求需要跨域可以查看：PHP Ajax 跨域问题解决方案。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `AJAX PHP` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
