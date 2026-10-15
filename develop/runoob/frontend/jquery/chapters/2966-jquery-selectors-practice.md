# jQuery：jQuery 选择器

- 来源：[jQuery 选择器](https://www.runoob.com/jquery/jquery-selectors.html)
- 分类：前端开发
- 技术：jQuery
- 笔记类型：练习笔记
- 章节序号：2966

## 本章内容

jQuery 选择器允许您对 HTML 元素组或单个元素进行操作。


## jQuery 选择器

jQuery 选择器允许您对 HTML 元素组或单个元素进行操作。

jQuery 选择器基于元素的 id、类、类型、属性、属性值等"查找"（或选择）HTML 元素。 它基于已经存在的 CSS 选择器，除此之外，它还有一些自定义的选择器。

jQuery 中所有选择器都以美元符号开头：$()。


## 元素选择器

jQuery 元素选择器基于元素名选取元素。

在页面中选取所有 <p> 元素:

实例

用户点击按钮后，所有 <p> 元素都隐藏：


## 实例

```text
$(document).ready(function(){
  $("button").click(function(){
    $("p").hide();
  });
});
```


## #id 选择器

jQuery #id 选择器通过 HTML 元素的 id 属性选取指定的元素。

页面中元素的 id 应该是唯一的，所以您要在页面中选取唯一的元素需要通过 #id 选择器。

通过 id 选取元素语法如下：

实例

当用户点击按钮后，有 id="test" 属性的元素将被隐藏：


## 实例

```text
$(document).ready(function(){
  $("button").click(function(){
    $("#test").hide();
  });
});
```


## .class 选择器

jQuery 类选择器可以通过指定的 class 查找元素。

语法如下：

实例

用户点击按钮后所有带有 class="test" 属性的元素都隐藏：


## 实例

```text
$(document).ready(function(){
  $("button").click(function(){
    $(".test").hide();
  });
});
```


## 更多实例


## 独立文件中使用 jQuery 函数

如果您的网站包含许多页面，并且您希望您的 jQuery 函数易于维护，那么请把您的 jQuery 函数放到独立的 .js 文件中。

当我们在教程中演示 jQuery 时，会将函数直接添加到 <head> 部分中。不过，把它们放到一个单独的文件中会更好，就像这样（通过 src 属性来引用文件）：


## 实例

```html
<head>
<script src="https://lf9-cdn-tos.bytecdntp.com/cdn/expire-1-M/jquery/1.10.2/jquery.min.js">
</script>
<script src="my_jquery_functions.js"></script>
</head>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jQuery 选择器` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
