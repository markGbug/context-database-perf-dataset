# HTML5：HTML 框架

- 来源：[HTML 框架](https://www.runoob.com/html/html-iframes.html)
- 分类：前端开发
- 技术：HTML5
- 笔记类型：练习笔记
- 章节序号：2695

## 本章内容

通过使用框架，你可以在同一个浏览器窗口中显示不止一个页面。

iframe语法:

```html
<iframe src="URL"></iframe>
```

该URL指向不同的网页。


## iframe - 设置高度与宽度

height 和 width 属性用来定义iframe标签的高度与宽度。

属性默认以像素为单位, 但是你可以指定其按比例显示 (如："80%")。


## 实例

```html
<iframe src="demo_iframe.htm" width="200" height="200"></iframe>
```


## iframe - 移除边框

frameborder 属性用于定义iframe表示是否显示边框。

设置属性值为 "0" 移除iframe的边框:


## 实例

```html
<iframe src="demo_iframe.htm" frameborder="0"></iframe>
```


## 使用 iframe 来显示目标链接页面

iframe 可以显示一个目标链接的页面

目标链接的属性必须使用 iframe 的属性，如下实例:


## 实例

```html
<iframe src="demo_iframe.htm" name="iframe_a"></iframe>
<p><a href="https://www.runoob.com" target="iframe_a" rel="noopener">RUNOOB.COM</a></p>
```


## HTML iframe 标签


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `HTML 框架` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
