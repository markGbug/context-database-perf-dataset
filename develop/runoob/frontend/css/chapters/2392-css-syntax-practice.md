# CSS：CSS 语法

- 来源：[CSS 语法](https://www.runoob.com/css/css-syntax.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：练习笔记
- 章节序号：2392

## 本章内容

## 实例

- 查看 实例 1
- 查看 实例 2


## CSS 实例

CSS 规则由两个主要的部分构成：选择器，以及一条或多条声明:

选择器通常是您需要改变样式的 HTML 元素。

每条声明由一个属性和一个值组成。

属性（property）是您希望设置的样式属性（style attribute）。每个属性有一个值。属性和值被冒号分开。


## CSS 实例

CSS声明总是以分号 ; 结束，声明总以大括号 {} 括起来:

```text
p {color:red;text-align:center;}
```

为了让CSS可读性更强，你可以每行只描述一个属性:


## 实例

```text
p
{
    color:red;
    text-align:center;
}
```


## CSS 注释

注释是用来解释你的代码，并且可以随意编辑它，浏览器会忽略它。

CSS注释以 /* 开始, 以 */ 结束, 实例如下:


## 实例

```text
/*这是个注释*/
p
{
    text-align:center;
    /*这是另一个注释*/
    color:black;
    font-family:arial;
}
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CSS 语法` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
