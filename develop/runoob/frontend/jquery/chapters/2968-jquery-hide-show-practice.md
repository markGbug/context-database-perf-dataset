# jQuery：jQuery 效果- 隐藏和显示

- 来源：[jQuery 隐藏/显示](https://www.runoob.com/jquery/jquery-hide-show.html)
- 分类：前端开发
- 技术：jQuery
- 笔记类型：练习笔记
- 章节序号：2968

## 本章内容

隐藏、显示、切换，滑动，淡入淡出，以及动画，哇哦！

点击 显示/隐藏面板

因为时间是宝贵的，我们提供快捷方便的学习方法。

在菜鸟教程,你可以学习需要的知识。


## 实例

jQuery hide() 简单的jQuery hide()方法演示。

jQuery hide() 另一个hide()实例。演示如何隐藏文本。


## jQuery hide() 和 show()

通过 jQuery，您可以使用 hide() 和 show() 方法来隐藏和显示 HTML 元素：


## 实例

```text
$("#hide").click(function(){
  $("p").hide();
});

$("#show").click(function(){
  $("p").show();
});
```

语法:

可选的 speed 参数规定隐藏/显示的速度，可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是隐藏或显示完成后所执行的函数名称。

下面的例子演示了带有 speed 参数的 hide() 方法：


## 实例

```text
$("button").click(function(){
  $("p").hide(1000);
});
```

下面的例子演示了带有 speed 参数的 hide() 方法，并使用回调函数：


## 实例

```text
$(document).ready(function(){
  $(".hidebtn").click(function(){
    $("div").hide(1000,"linear",function(){
      alert("Hide() 方法已完成!");
    });
  });
});
```

第二个参数是一个字符串，表示过渡使用哪种缓动函数。（译者注：jQuery自身提供"linear" 和 "swing"，其他可以使用相关的插件）。


## jQuery toggle()

通过 jQuery，您可以使用 toggle() 方法来切换 hide() 和 show() 方法。

显示被隐藏的元素，并隐藏已显示的元素：


## 实例

```text
$("button").click(function(){
  $("p").toggle();
});
```

语法:

可选的 speed 参数规定隐藏/显示的速度，可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是隐藏或显示完成后所执行的函数名称。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jQuery 隐藏/显示` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
