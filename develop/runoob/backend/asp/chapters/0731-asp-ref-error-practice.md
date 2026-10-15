# ASP：ASP ASPError 对象

- 来源：[ASP Error](https://www.runoob.com/asp/asp-ref-error.html)
- 分类：后端开发
- 技术：ASP
- 笔记类型：练习笔记
- 章节序号：0731

## 本章内容

ASPError 对象用于显示在 ASP 文件的脚本中发生的错误信息。


## ASPError 对象

ASPError 对象在 ASP 3.0 中生效，且在 IIS5 及更高版本中可用。

ASPError 对象用于显示在 ASP 文件的脚本中发生的任何错误的详细信息。

注释：当 Server.GetLastError 被调用时，ASPError 对象就会被创建，因此只能通过使用 Server.GetLastError 方法来访问错误信息。

ASPError 对象的属性描述如下（所有属性都是可读的）：


### 属性


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ASP Error` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
