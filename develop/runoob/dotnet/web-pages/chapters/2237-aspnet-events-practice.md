# Web Pages：ASP.NET Web Forms - 事件

- 来源：[WebForms 事件](https://www.runoob.com/aspnet/aspnet-events.html)
- 分类：.NET
- 技术：Web Pages
- 笔记类型：练习笔记
- 章节序号：2237

## 本章内容

事件句柄是一种针对给定事件来执行代码的子例程。


## ASP.NET - 事件句柄

请看下面的代码：

上面的代码将在何时被执行？答案是："不知道..."。


## Page_Load 事件

Page_Load 事件是 ASP.NET 可理解的众多事件之一。Page_Load 事件会在页面加载时被触发， ASP.NET 将自动调用 Page_Load 子例程，并执行其中的代码：


## 实例

注释：Page_Load 事件不包含对象引用或事件参数！


## Page.IsPostBack 属性

Page_Load 子例程会在页面每次加载时运行。如果您只想在页面第一次加载时执行 Page_Load 子例程中的代码，那么您可以使用 Page.IsPostBack 属性。如果 Page.IsPostBack 属性设置为 false，则页面第一次被载入，如果设置为 true，则页面被传回到服务器（比如，通过点击表单上的按钮）：


## 实例

上面的实例仅在页面第一次加载时显示 "The date and time is...." 消息。当用户点击 Submit 按钮是，submit 子例程将会在第二个 label 中写入 "Hello World!"，但是第一个 label 中的日期和时间不会改变。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `WebForms 事件` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
