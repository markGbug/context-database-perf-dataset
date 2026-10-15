# ASP：ASP Cookies

- 来源：[ASP Cookies](https://www.runoob.com/asp/asp-cookies.html)
- 分类：后端开发
- 技术：ASP
- 笔记类型：练习笔记
- 章节序号：0720

## 本章内容

cookie 常用于识别用户。


## 尝试一下 - 实例

Welcome cookie 本例演示如何创建 Welcome cookie。


## Cookie 是什么？

cookie 常用用于识别用户。cookie 是一种服务器留在用户计算机上的小文件。每当同一台计算机通过浏览器请求页面时，这台计算机将会发送 cookie。通过 ASP，您能够创建并取回 cookie 的值。


## 如何创建 Cookie？

"Response.Cookies" 命令用于创建 cookie。

注释：Response.Cookies 命令必须出现在 <html> 标签之前。

在下面的实例中，我们将创建一个名为 "firstname" 的 cookie，并将其赋值为 "Alex"：

向 cookie 分配属性也是可以的，比如设置 cookie 的失效时间：


## 如何取回 Cookie 的值？

"Request.Cookies" 命令用于取回 cookie 的值。

在下面的实例中，我们取回了名为 "firstname" 的 cookie 的值，并把值显示到了页面上：

输出： Firstname=Alex


## 带有键的 Cookie

如果一个 cookie 包含多个值的集合，我们就可以说 cookie 带有键（Keys）。

在下面的实例中，我们将创建一个名为 "user" 的 cookie 集合。"user" cookie 带有包含用户信息的键：


## 读取所有的 Cookie

请阅读下面的代码：

假设您的服务器将上面所有的 cookie 传给了某个用户。

现在，我们需要读取这些传给某个用户的所有的 cookie。下面的实例向您演示了如何做到这一点（请注意，下面的代码通过 HasKeys 属性检查 cookie 是否带有键）：

输出：

firstname=Alex

user:firstname=John user:lastname=Smith user:country=Norway user:age=25


## 如果浏览器不支持 Cookie 该怎么办？

如果您的应用程序需要与不支持 cookie 的浏览器打交道，那么您不得不使用其他的办法在您的应用程序中的页面之间传递信息。这里有两种办法：


### 1. 向 URL 添加参数

您可以向 URL 添加参数：

然后在 "welcome.asp" 文件中取回这些值，如下所示：


### 2. 使用表单

您可以使用表单。当用户点击 Submit 按钮时，表单会把用户输入传给 "welcome.asp" ：

然后在 "welcome.asp" 文件中取回这些值，如下所示：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ASP Cookies` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
