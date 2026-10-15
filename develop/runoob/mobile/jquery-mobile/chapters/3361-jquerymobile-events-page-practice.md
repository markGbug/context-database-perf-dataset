# jQuery Mobile：jQuery Mobile 页面事件

- 来源：[jQuery Mobile页面事件](https://www.runoob.com/jquerymobile/jquerymobile-events-page.html)
- 分类：移动开发
- 技术：jQuery Mobile
- 笔记类型：练习笔记
- 章节序号：3361

## 本章内容

## jQuery Mobile 页面事件

在 jQuery Mobile 中与页面打交道的事件被分为四类：

- Page Initialization - 在页面创建前，当页面创建时，以及在页面初始化之后
- Page Load/Unload - 当外部页面加载时、卸载时或遭遇失败时
- Page Transition - 在页面过渡之前和之后
- Page Change - 当页面被更改，或遭遇失败时

如需关于所有 jQuery Mobile 事件的完整信息，请访问我们的 jQuery Mobile 事件参考手册。


## jQuery Mobile Initialization 事件

当 jQuery Mobile 中的一张典型页面进行初始化时，它会经历三个阶段：

- 在页面创建前
- 页面创建
- 页面初始化

每个阶段触发的事件都可用于插入或操作代码。

下面的例子演示在 jQuery Mobile 中创建页面时，何时触发每种事件：


## 实例


## jQuery Mobile Load 事件

页面加载事件属于外部页面。

无论外部页面何时载入 DOM，将触发两个事件。第一个是 pagebeforeload，第二个是 pageload （成功）或 pageloadfailed（失败）。

下表中解释了这些事件：

下列演示 pageload 和 pagloadfailed 事件的工作原理：


## 实例


## jQuery Mobile 过渡事件

我们还可以在从一页过渡到下一页时使用事件。

页面过渡涉及两个页面：一张"来"的页面和一张"去"的页面 - 这些过渡使当前活动页面（"来的"页面）到新页面（"去的"页面的改变过程变得更加动感。

下列演示了过渡时间的工作原理：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jQuery Mobile页面事件` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
