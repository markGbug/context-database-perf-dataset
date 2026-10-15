# 知识点 65144：jQuery UI：拖动（Draggable） - 约束运动

- 来源：[拖动（Draggable）](https://www.runoob.com/jqueryui/example-draggable.html)
- 来源章节：[2935-example-draggable-study.md](../chapters/2935-example-draggable-study.md)
- 分类：前端开发
- 技术：jQuery UI
- 所在小节：约束运动
- 知识类型：代码
- 原章节序号：2935

## 原文片段

```text
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>jQuery UI 拖动（Draggable） - 约束运动</title>
  <link rel="stylesheet" href="//code.jquery.com/ui/1.10.4/themes/smoothness/jquery-ui.css">
  <script src="//code.jquery.com/jquery-1.9.1.js"></script>
  <script src="//code.jquery.com/ui/1.10.4/jquery-ui.js"></script>
  <link rel="stylesheet" href="http://jqueryui.com/resources/demos/style.css">
  <style>
  .draggable { width: 90px; height: 90px; padding: 0.5em; float: left; margin: 0 10px 10px 0; }
  #draggable, #draggable2 { margin-bottom:20px; }
  #draggable { cursor: n-resize; }
  #draggable2 { cursor: e-resize; }
  #containment-wrapper { width: 95%; height:150px; border:2px solid #ccc; padding: 10px; }
  h3 { clear: left; }
  </style>
  <script>
  $(function() {
    $( "#draggable" ).draggable({ axis: "y" });
    $( "#draggable2" ).draggable({ axis: "x" });

    $( "#draggable3" ).draggable({ containment: "#containment-wrapper", scroll: false });
    $( "#draggable5" ).draggable({ containment: "parent" });
  });
  </script>
</head>
<body>

<h3>沿着轴约束运动：</h3>

<div id="draggable" class="draggable ui-widget-content">
  <p>只能垂直拖拽</p>
</div>

<div id="draggable2" class="draggable ui-widget-content">
  <p>只能水平拖拽</p>
</div>

<h3>或者在另一个 DOM 元素中约束运动：</h3>
<div id="containment-wrapper">
  <div id="draggable3" class="draggable ui-widget-content">
    <p>我被约束在盒子里</p>
  </div>

  <div class="draggable ui-widget-content">
    <p id="draggable5" class="ui-widget-header">我被约束在父元素内</p>
  </div>
</div>


</body>
</html>
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `约束运动` 这一小节和 `拖动（Draggable）` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
