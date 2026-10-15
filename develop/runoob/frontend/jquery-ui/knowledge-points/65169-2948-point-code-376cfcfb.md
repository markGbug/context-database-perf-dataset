# 知识点 65169：jQuery UI：旋转器（Spinner） - 小数

- 来源：[旋转器（Spinner）](https://www.runoob.com/jqueryui/example-spinner.html)
- 来源章节：[2948-example-spinner-practice.md](../chapters/2948-example-spinner-practice.md)
- 分类：前端开发
- 技术：jQuery UI
- 所在小节：小数
- 知识类型：代码
- 原章节序号：2948

## 原文片段

```text
<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <title>jQuery UI 旋转器（Spinner） - 小数</title>
  <link rel="stylesheet" href="//code.jquery.com/ui/1.10.4/themes/smoothness/jquery-ui.css">
  <script src="//code.jquery.com/jquery-1.9.1.js"></script>
  <script src="/static/js/jqueryui/resources/demos/external/jquery.mousewheel.js"></script>
  <script src="/static/js/jqueryui/resources/demos/external/globalize.js"></script>
  <script src="/static/js/jqueryui/resources/demos/external/globalize.culture.de-DE.js"></script>
  <script src="/static/js/jqueryui/resources/demos/external/globalize.culture.ja-JP.js"></script>
  <script src="//code.jquery.com/ui/1.10.4/jquery-ui.js"></script>
  <link rel="stylesheet" href="http://jqueryui.com/resources/demos/style.css">
  <script>
  $(function() {
    $( "#spinner" ).spinner({
      step: 0.01,
      numberFormat: "n"
    });

    $( "#culture" ).change(function() {
      var current = $( "#spinner" ).spinner( "value" );
      Globalize.culture( $(this).val() );
      $( "#spinner" ).spinner( "value", current );
    });
  });
  </script>
</head>
<body>

<p>
  <label for="spinner">小数旋转器：</label>
  <input id="spinner" name="spinner" value="5.06">
</p>
<p>
  <label for="culture">选择一种用于格式化的文化：</label>
  <select id="culture">
    <option value="en-EN" selected="selected">English</option>
    <option value="de-DE">German</option>
    <option value="ja-JP">Japanese</option>
  </select>
</p>
</body>
</html>
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `小数` 这一小节和 `旋转器（Spinner）` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
