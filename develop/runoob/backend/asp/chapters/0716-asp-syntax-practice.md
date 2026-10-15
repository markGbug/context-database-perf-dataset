# ASP：ASP 基本语法规则

- 来源：[ASP 语法](https://www.runoob.com/asp/asp-syntax.html)
- 分类：后端开发
- 技术：ASP
- 笔记类型：练习笔记
- 章节序号：0716

## 本章内容

在我们的 ASP 教程中，每个实例都提供隐藏的 ASP 源代码。这样会使您更容易理解它们的工作原理。


## 向浏览器写输出

ASP 文件通常包含 HTML 标签，就像 HTML 文件。然而，ASP 文件也能包含服务器脚本，这些脚本被分隔符 <% 和 %> 包围起来。

服务器脚本在服务器上执行，可包含你所选用的脚本语言的合法的表达式、语句、程序或者运算符。


### response.write 命令

response.write 命令用来向浏览器写输出。下面的实例向浏览器传送了一段文本："Hello World"：


## 实例

还有一种 response.write 命令的简写方法。下面的实例也是向浏览器传送了一段文本："Hello World"：


## 实例


## 在 ASP 中使用 VBScript

您可以在 ASP 中使用若干种脚本语言。然而，默认的脚本语言是 VBScript：

上面的实例向文档的 body 部分写入了文本 "Hello World!"。


## 在 ASP 中使用 JavaScript

如果需要设置 JavaScript 为某个特定页面的默认脚本语言，您必须在页面的顶部插入一行语言说明：

注释：与 VBScript 不同，JavaScript 对大小写敏感！你必须根据 JavaScript 的需要使用不同的大小写字母编写您的 ASP 代码。


## 其他的脚本语言

ASP 与 VBScript 和 JScript（JScript 是微软的 JavaScript 实现）的配合是原生性的。如果您想要使用其他语言编写脚本，比如 PERL、REXX 或者 Python，您必须安装相应的脚本引擎。


## 更多实例

给文本添加一些 HTML 标签


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ASP 语法` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
