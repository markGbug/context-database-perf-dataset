# ASP：AJAX 数据库实例

- 来源：[AJAX 数据库](https://www.runoob.com/asp/asp-ajax-database.html)
- 分类：后端开发
- 技术：ASP
- 笔记类型：学习笔记
- 章节序号：0745

## 本章内容

AJAX 可用来与数据库进行交互式通信。


## AJAX 数据库实例

下面的实例将演示网页如何通过 AJAX 从数据库读取信息：


## 实例


## 实例解释 - HTML 页面

当用户在上面的下拉列表中选择某位客户时，会执行名为 "showCustomer()" 的函数。该函数由 "onchange" 事件触发：

源代码解释：

如果没有选择客户（str.length==0），那么该函数会清空 txtHint 占位符，然后退出该函数。

如果已选择一位客户，则 showCustomer() 函数会执行以下步骤：

- 创建 XMLHttpRequest 对象
- 创建在服务器响应就绪时执行的函数
- 向服务器上的文件发送请求
- 请注意添加到 URL 末端的参数（q）（包含下拉列表的内容）


## ASP 文件

上面这段通过 JavaScript 调用的服务器页面是名为 "getcustomer.asp" 的 ASP 文件。

"getcustomer.asp" 中的源代码会运行一次针对数据库的查询，然后在 HTML 表格中返回结果：


## 复习重点

- 能说明 `AJAX 数据库` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
