# 知识点 26504：jQuery UI：.addClass() - .addClass() 演示

- 来源：[.addClass()](https://www.runoob.com/jqueryui/example-addclass.html)
- 来源章节：[2955-example-addclass-study.md](../chapters/2955-example-addclass-study.md)
- 分类：前端开发
- 技术：jQuery UI
- 所在小节：.addClass() 演示
- 知识类型：代码
- 原章节序号：2955

## 原文片段

```text
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>jQuery UI 特效 - .addClass() 演示</title>
  <link rel="stylesheet" href="//code.jquery.com/ui/1.10.4/themes/smoothness/jquery-ui.css">
  <script src="//code.jquery.com/jquery-1.9.1.js"></script>
  <script src="//code.jquery.com/ui/1.10.4/jquery-ui.js"></script>
  <link rel="stylesheet" href="http://jqueryui.com/resources/demos/style.css">
  <style>
    .toggler { width: 500px; height: 200px; position: relative; }
    #button { padding: .5em 1em; text-decoration: none; }
    #effect { width: 240px;  padding: 1em;  font-size: 1.2em; border: 1px solid #000; background: #eee; color: #333; }
    .newClass { text-indent: 40px; letter-spacing: .4em; width: 410px; height: 100px; padding: 30px; margin: 10px; font-size: 1.6em; }
  </style>
  <script>
  $(function() {
    $( "#button" ).click(function() {
      $( "#effect" ).addClass( "newClass", 1000, callback );
      return false;
    });

    function callback() {
      setTimeout(function() {
        $( "#effect" ).removeClass( "newClass" );
      }, 1500 );
    }
  });
  </script>
</head>
<body>

<div class="toggler">
  <div id="effect" class="ui-corner-all">
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

- `.addClass() 演示` 这一小节和 `.addClass()` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
