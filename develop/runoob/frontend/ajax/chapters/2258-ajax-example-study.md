# AJAX：AJAX 实例

- 来源：[AJAX 实例](https://www.runoob.com/ajax/ajax-example.html)
- 分类：前端开发
- 技术：AJAX
- 笔记类型：学习笔记
- 章节序号：2258

## 本章内容

为了帮助您理解 AJAX 的工作原理，我们创建了一个小型的 AJAX 应用程序:


## 实例


## 使用 AJAX 修改该文本内容


## AJAX 实例解析

上面的 AJAX 应用程序包含一个 div 和一个按钮。

div 部分用于显示来自服务器的信息。当按钮被点击时，它负责调用名为 loadXMLDoc() 的函数：

```html
<div id="myDiv"><h2>使用 AJAX 修改该文本内容</h2></div>
<button type="button" onclick="loadXMLDoc()">修改内容</button>
```

接下来，在页面的 head 部分添加一个 <script> 标签。该标签中包含了这个 loadXMLDoc() 函数：

```html
<head>
<script>
function loadXMLDoc()
{
    .... AJAX 脚本执行 ...
}
</script>
</head>
```

下面的章节会为您讲解 AJAX 的工作原理。


## 复习重点

- 能说明 `AJAX 实例` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
