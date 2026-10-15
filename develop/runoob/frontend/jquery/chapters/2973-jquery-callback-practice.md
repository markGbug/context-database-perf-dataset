# jQuery：jQuery Callback 方法

- 来源：[jQuery Callback](https://www.runoob.com/jquery/jquery-callback.html)
- 分类：前端开发
- 技术：jQuery
- 笔记类型：练习笔记
- 章节序号：2973

## 本章内容

Callback 函数在当前动画 100% 完成之后执行。


## jQuery 动画的问题

许多 jQuery 函数涉及动画。这些函数也许会将 speed 或 duration 作为可选参数。

例子：$("p").hide("slow")

speed 或 duration 参数可以设置许多不同的值，比如 "slow", "fast", "normal" 或毫秒。

实例

以下实例在隐藏效果完全实现后回调函数:


## 使用 callback 实例

```text
$("button").click(function(){
  $("p").hide("slow",function(){
    alert("段落现在被隐藏了");
  });
});
```

以下实例没有回调函数，警告框会在隐藏效果完成前弹出：


## 没有 callback(回调)

```text
$("button").click(function(){
  $("p").hide(1000);
  alert("段落现在被隐藏了");
});
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jQuery Callback` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
