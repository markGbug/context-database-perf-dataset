# jQuery：jQuery 语法

- 来源：[jQuery 语法](https://www.runoob.com/jquery/jquery-syntax.html)
- 分类：前端开发
- 技术：jQuery
- 笔记类型：学习笔记
- 章节序号：2965

## 本章内容

通过 jQuery，您可以选取（查询，query） HTML 元素，并对它们执行"操作"（actions）。


## jQuery 语法

jQuery 语法是通过选取 HTML 元素，并对选取的元素执行某些操作。

基础语法： $(selector).action()

- 美元符号定义 jQuery
- 选择符（selector）"查询"和"查找" HTML 元素
- jQuery 的 action() 执行对元素的操作

实例:

- $(this).hide() - 隐藏当前元素
- $("p").hide() - 隐藏所有 <p> 元素
- $("p.test").hide() - 隐藏所有 class="test" 的 <p> 元素
- $("#test").hide() - 隐藏 id="test" 的元素


## 文档就绪事件

您也许已经注意到在我们的实例中的所有 jQuery 函数位于一个 document ready 函数中：

```text
$(document).ready(function(){

   // 开始写 jQuery 代码...

});
```

这是为了防止文档在完全加载（就绪）之前运行 jQuery 代码，即在 DOM 加载完成后才可以对 DOM 进行操作。

如果在文档没有完全加载之前就运行函数，操作可能失败。下面是两个具体的例子：

- 试图隐藏一个不存在的元素
- 获得未完全加载的图像的大小

提示：简洁写法（与以上写法效果相同）:

```text
$(function(){

   // 开始写 jQuery 代码...

});
```

以上两种方式你可以选择你喜欢的方式实现文档就绪后执行 jQuery 方法。


## 复习重点

- 能说明 `jQuery 语法` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
