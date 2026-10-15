# 知识点 83555：jQuery UI：自动完成（Autocomplete） - 包含重音

- 来源：[自动完成（Autocomplete）](https://www.runoob.com/jqueryui/example-autocomplete.html)
- 来源章节：[2941-example-autocomplete-practice.md](../chapters/2941-example-autocomplete-practice.md)
- 分类：前端开发
- 技术：jQuery UI
- 所在小节：包含重音
- 知识类型：代码
- 原章节序号：2941

## 原文片段

```text
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>jQuery UI 自动完成（Autocomplete） - 包含重音</title>
  <link rel="stylesheet" href="//code.jquery.com/ui/1.10.4/themes/smoothness/jquery-ui.css">
  <script src="//code.jquery.com/jquery-1.9.1.js"></script>
  <script src="//code.jquery.com/ui/1.10.4/jquery-ui.js"></script>
  <link rel="stylesheet" href="http://jqueryui.com/resources/demos/style.css">
  <script>
  $(function() {
    var names = [ "Jörn Zaefferer", "Scott González", "John Resig" ];

    var accentMap = {
      "á": "a",
      "ö": "o"
    };
    var normalize = function( term ) {
      var ret = "";
      for ( var i = 0; i < term.length; i++ ) {
        ret += accentMap[ term.charAt(i) ] || term.charAt(i);
      }
      return ret;
    };

    $( "#developer" ).autocomplete({
      source: function( request, response ) {
        var matcher = new RegExp( $.ui.autocomplete.escapeRegex( request.term ), "i" );
        response( $.grep( names, function( value ) {
          value = value.label || value.value || value;
          return matcher.test( value ) || matcher.test( normalize( value ) );
        }) );
      }
    });
  });
  </script>
</head>
<body>

<div class="ui-widget">
  <form>
  <label for="developer">开发人员：</label>
  <input id="developer">
  </form>
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

- `包含重音` 这一小节和 `自动完成（Autocomplete）` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
