# 知识点 83572：jQuery UI：标签页（Tabs） - 通过 Ajax 获取内容

- 来源：[标签页（Tabs）](https://www.runoob.com/jqueryui/example-tabs.html)
- 来源章节：[2949-example-tabs-study.md](../chapters/2949-example-tabs-study.md)
- 分类：前端开发
- 技术：jQuery UI
- 所在小节：通过 Ajax 获取内容
- 知识类型：代码
- 原章节序号：2949

## 原文片段

```text
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>jQuery UI 标签页（Tabs） - 通过 Ajax 获取内容</title>
  <link rel="stylesheet" href="//code.jquery.com/ui/1.10.4/themes/smoothness/jquery-ui.css">
  <script src="//code.jquery.com/jquery-1.9.1.js"></script>
  <script src="//code.jquery.com/ui/1.10.4/jquery-ui.js"></script>
  <link rel="stylesheet" href="http://jqueryui.com/resources/demos/style.css">
  <script>
  $(function() {
    $( "#tabs" ).tabs({
      beforeLoad: function( event, ui ) {
        ui.jqXHR.error(function() {
          ui.panel.html(
            "不能加载该标签页。如果这不是一个演示。" +
            "我们会尽快修复这个问题。" );
        });
      }
    });
  });
  </script>
</head>
<body>

<div id="tabs">
  <ul>
    <li><a href="#tabs-1">预加载</a></li>
    <li><a href="ajax/content1.html">标签 1</a></li>
    <li><a href="ajax/content2.html">标签 2</a></li>
    <li><a href="ajax/content3-slow.php">标签 3 （慢的）</a></li>
    <li><a href="ajax/content4-broken.php">标签 4 （损坏的）</a></li>
  </ul>
  <div id="tabs-1">
    <p>Proin elit arcu, rutrum commodo, vehicula tempus, commodo a, risus. Curabitur nec arcu. Donec sollicitudin mi sit amet mauris. Nam elementum quam ullamcorper ante. Etiam aliquet massa et lorem. Mauris dapibus lacus auctor risus. Aenean tempor ullamcorper leo. Vivamus sed magna quis ligula eleifend adipiscing. Duis orci. Aliquam sodales tortor vitae ipsum. Aliquam nulla. Duis aliquam molestie erat. Ut et mauris vel pede varius sollicitudin. Sed ut dolor nec orci tincidunt interdum. Phasellus ipsum. Nunc tristique tempus lectus.</p>
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

- `通过 Ajax 获取内容` 这一小节和 `标签页（Tabs）` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
