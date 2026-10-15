# JavaScript：JavaScript if...Else 语句

- 来源：[JavaScript 条件语句](https://www.runoob.com/js/js-if-else.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：练习笔记
- 章节序号：2772

## 本章内容

条件语句用于基于不同的条件来执行不同的动作。


## 条件语句

通常在写代码时，您总是需要为不同的决定来执行不同的动作。您可以在代码中使用条件语句来完成该任务。

在 JavaScript 中，我们可使用以下条件语句：

- if 语句 - 只有当指定条件为 true 时，使用该语句来执行代码
- if...else 语句 - 当条件为 true 时执行代码，当条件为 false 时执行其他代码
- if...else if....else 语句- 使用该语句来选择多个代码块之一来执行
- switch 语句 - 使用该语句来选择多个代码块之一来执行


## if 语句

只有当指定条件为 true 时，该语句才会执行代码。


### 语法

请使用小写的 if。使用大写字母（IF）会生成 JavaScript 错误！


## 实例

当时间小于 20:00 时，生成问候 "Good day"：

```text
if (time<20)
{
    x="Good day";
}
```

请注意，在这个语法中，没有 ..else..。您已经告诉浏览器只有在指定条件为 true 时才执行代码。


## if...else 语句

请使用 if....else 语句在条件为 true 时执行代码，在条件为 false 时执行其他代码。


### 语法


## 实例

当时间小于 20:00 时，生成问候 "Good day"，否则生成问候 "Good evening"。

```text
if (time<20)
{
    x="Good day";
}
else
{
    x="Good evening";
}
```

x 的结果是：


## if...else if...else 语句

使用 if....else if...else 语句来选择多个代码块之一来执行。


### 语法


## 实例

如果时间小于 10:00，则生成问候 "Good morning"，如果时间大于 10:00 小于 20:00，则生成问候 "Good day"，否则生成问候 "Good evening"：

```html
if (time<10)
{
    document.write("<b>早上好</b>");
}
else if (time>=10 && time<20)
{
    document.write("<b>今天好</b>");
}
else
{
    document.write("<b>晚上好!</b>");
}
```

x 的结果是：


## 更多实例

随机链接 这个实例演示了一个链接，当您点击链接时，会带您到不同的地方去。每种机会都是 50% 的概率。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `JavaScript 条件语句` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
