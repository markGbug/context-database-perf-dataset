# jQuery：jQuery 遍历 - 后代

- 来源：[jQuery 后代](https://www.runoob.com/jquery/jquery-traversing-descendants.html)
- 分类：前端开发
- 技术：jQuery
- 笔记类型：练习笔记
- 章节序号：2984

## 本章内容

后代是子、孙、曾孙等等。

通过 jQuery，您能够向下遍历 DOM 树，以查找元素的后代。


## 向下遍历 DOM 树

下面是两个用于向下遍历 DOM 树的 jQuery 方法：

- children()
- find()


## jQuery children() 方法

children() 方法返回被选元素的所有直接子元素。

该方法只会向下一级对 DOM 树进行遍历。

下面的例子返回每个 <div> 元素的所有直接子元素：


## 实例

```text
$(document).ready(function(){
  $("div").children();
});
```

您也可以使用可选参数来过滤对子元素的搜索。

下面的例子返回类名为 "1" 的所有 <p> 元素，并且它们是 <div> 的直接子元素：


## 实例

```text
$(document).ready(function(){
  $("div").children("p.1");
});
```


## jQuery find() 方法

find() 方法返回被选元素的后代元素，一路向下直到最后一个后代。

下面的例子返回属于 <div> 后代的所有 <span> 元素：


## 实例

```text
$(document).ready(function(){
  $("div").find("span");
});
```

下面的例子返回 <div> 的所有后代：


## 实例

```text
$(document).ready(function(){
  $("div").find("*");
});
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jQuery 后代` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
