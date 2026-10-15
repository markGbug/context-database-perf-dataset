# HTML：HTML 脚本

- 来源：[HTML 脚本](https://www.runoob.com/html/html-scripts.html)
- 分类：前端开发
- 技术：HTML
- 笔记类型：练习笔记
- 章节序号：2623

## 本章内容

JavaScript 使 HTML 页面具有更强的动态和交互性。


## 在线实例

插入一段脚本 如何将脚本插入 HTML 文档。

使用 <noscript> 标签 如何应对不支持脚本或禁用脚本的浏览器。


## HTML <script> 标签

<script> 标签用于定义客户端脚本，比如 JavaScript。

<script> 元素既可包含脚本语句，也可通过 src 属性指向外部脚本文件。

JavaScript 最常用于图片操作、表单验证以及内容动态更新。

下面的脚本会向浏览器输出"Hello World!"：


## 实例

```html
<script>
document.write("Hello World!");
</script>
```

Tip: 学习更多关于Javascript教程，请查看JavaScript 教程!


## HTML<noscript> 标签

<noscript> 标签提供无法使用脚本时的替代内容，比方在浏览器禁用脚本时，或浏览器不支持客户端脚本时。

<noscript>元素可包含普通 HTML 页面的 body 元素中能够找到的所有元素。

只有在浏览器不支持脚本或者禁用脚本时，才会显示 <noscript> 元素中的内容：


## 实例

```html
<script>
document.write("Hello World!")
</script>
<noscript>抱歉，你的浏览器不支持 JavaScript!</noscript>
```


## JavaScript体验(来自本站javascript教程)

JavaScript实例代码:


## JavaScript可以直接在HTML输出:

```html
document.write("<p>这是一个段落。</p>");
```


## JavaScript事件响应:

```html
<button type="button" onclick="myFunction()">点我！</button>
```


## JavaScript处理 HTML 样式:

```text
document.getElementById("demo").style.color="#ff0000";
```


## HTML 脚本标签


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `HTML 脚本` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
