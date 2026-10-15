# jQuery：jQuery 遍历 - 祖先

- 来源：[jQuery 祖先](https://www.runoob.com/jquery/jquery-traversing-ancestors.html)
- 分类：前端开发
- 技术：jQuery
- 笔记类型：练习笔记
- 章节序号：2983

## 本章内容

祖先是父、祖父或曾祖父等等。

通过 jQuery，您能够向上遍历 DOM 树，以查找元素的祖先。


## 向上遍历 DOM 树

这些 jQuery 方法很有用，它们用于向上遍历 DOM 树：

- parent()
- parents()
- parentsUntil()


## jQuery parent() 方法

parent() 方法返回被选元素的直接父元素。

该方法只会向上一级对 DOM 树进行遍历。

下面的例子返回每个 <span> 元素的直接父元素：


## 实例

```text
$(document).ready(function(){
  $("span").parent();
});
```


## jQuery parents() 方法

parents() 方法返回被选元素的所有祖先元素，它一路向上直到文档的根元素 (<html>)。

下面的例子返回所有 <span> 元素的所有祖先：


## 实例

```text
$(document).ready(function(){
  $("span").parents();
});
```

您也可以使用可选参数来过滤对祖先元素的搜索。

下面的例子返回所有 <span> 元素的所有祖先，并且它是 <ul> 元素：


## 实例

```text
$(document).ready(function(){
  $("span").parents("ul");
});
```


## jQuery parentsUntil() 方法

parentsUntil() 方法返回介于两个给定元素之间的所有祖先元素。

下面的例子返回介于 <span> 与 <div> 元素之间的所有祖先元素：


## 实例

```text
$(document).ready(function(){
  $("span").parentsUntil("div");
});
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jQuery 祖先` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
