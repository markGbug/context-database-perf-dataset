# ASP：ASP 子程序

- 来源：[ASP 程序](https://www.runoob.com/asp/asp-procedures.html)
- 分类：后端开发
- 技术：ASP
- 笔记类型：练习笔记
- 章节序号：0718

## 本章内容

在 ASP 中，您可通过 VBScript 调用 JavaScript 子程序，反之亦然。


## 子程序

ASP 源代码可包含子程序和函数：


## 实例

将 <%@ language="language" %> 这一行写在 <html> 标签的上面，就可以使用另一种脚本语言来编写子程序或者函数：


## 实例


## VBScript 与 JavaScript 的不同

当从一个用 VBScript 编写的 ASP 文件中调用 VBScript 或者 JavaScript 子程序时，可以使用 "call" 关键词，后面跟着子程序名称。假如子程序需要参数，当使用 "call" 关键词时，参数必须包含在括号内。假如您省略了 "call" 关键词，则参数不必包含在括号内。如果子程序没有参数，那么括号则是可选的。

当从一个用 JavaScript 编写的 ASP 文件中调用 VBScript 或者 JavaScript 子程序时，必须在子程序名后使用括号。


## 更多实例

使用 VBScript 调用子程序 本例演示如何在一个 ASP 文件中调用 VBScript 子程序和 JavaScript 子程序。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ASP 程序` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
