# 知识点 26509：jQuery UI：.switchClass() - .switchClass() 演示

- 来源：[.switchClass()](https://www.runoob.com/jqueryui/example-switchclass.html)
- 来源章节：[2958-example-switchclass-practice.md](../chapters/2958-example-switchclass-practice.md)
- 分类：前端开发
- 技术：jQuery UI
- 所在小节：.switchClass() 演示
- 知识类型：代码
- 原章节序号：2958

## 原文片段

```text
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>jQuery UI 特效 - .switchClass() 演示</title>
  <link rel="stylesheet" href="//code.jquery.com/ui/1.10.4/themes/smoothness/jquery-ui.css">
  <script src="//code.jquery.com/jquery-1.9.1.js"></script>
  <script src="//code.jquery.com/ui/1.10.4/jquery-ui.js"></script>
  <link rel="stylesheet" href="http://jqueryui.com/resources/demos/style.css">
  <style>
  .toggler { width: 500px; height: 200px; position: relative; }
  #button { padding: .5em 1em; text-decoration: none; }
  #effect { position: relative; }
  .newClass { width: 240px;  padding: 1em; letter-spacing: 0; font-size: 1.2em; margin: 0; }
  .anotherNewClass { text-indent: 40px; letter-spacing: .4em; width: 410px; height: 100px; padding: 30px; margin: 10px; font-size: 1.6em; }
  </style>
  <script>
  $(function() {
    $( "#button" ).click(function(){
      $( ".newClass" ).switchClass( "newClass", "anotherNewClass", 1000 );
      $( ".anotherNewClass" ).switchClass( "anotherNewClass", "newClass", 1000 );
      return false;
    });
  });
  </script>
</head>
<body>

<div class="toggler">
  <div id="effect" class="newClass ui-corner-all">
      Etiam libero neque, luctus a, eleifend nec, semper at, lorem. Sed pede.
  </div>
</div>
<a href="#" id="button" class="ui-state-default ui-corner-all">运行特效</a>


</body>
</html>
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `.switchClass() 演示` 这一小节和 `.switchClass()` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
