# 知识点 74468：jQuery UI：滑块（Slider） - 多个滑块

- 来源：[滑块（Slider）](https://www.runoob.com/jqueryui/example-slider.html)
- 来源章节：[2947-example-slider-practice.md](../chapters/2947-example-slider-practice.md)
- 分类：前端开发
- 技术：jQuery UI
- 所在小节：多个滑块
- 知识类型：代码
- 原章节序号：2947

## 原文片段

```text
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>jQuery UI 滑块（Slider） - 多个滑块</title>
  <link rel="stylesheet" href="//code.jquery.com/ui/1.10.4/themes/smoothness/jquery-ui.css">
  <script src="//code.jquery.com/jquery-1.9.1.js"></script>
  <script src="//code.jquery.com/ui/1.10.4/jquery-ui.js"></script>
  <link rel="stylesheet" href="http://jqueryui.com/resources/demos/style.css">
  <style>
  #eq span {
    height:120px; float:left; margin:15px
  }
  </style>
  <script>
  $(function() {
    // 设置主音量
    $( "#master" ).slider({
      value: 60,
      orientation: "horizontal",
      range: "min",
      animate: true
    });
    // 设置图形均衡器
    $( "#eq > span" ).each(function() {
      // 从标记读取初始值并删除
      var value = parseInt( $( this ).text(), 10 );
      $( this ).empty().slider({
        value: value,
        range: "min",
        animate: true,
        orientation: "vertical"
      });
    });
  });
  </script>
</head>
<body>

<p class="ui-state-default ui-corner-all ui-helper-clearfix" style="padding:4px;">
  <span class="ui-icon ui-icon-volume-on" style="float:left; margin:-2px 5px 0 0;"></span>
  主音量
</p>

<div id="master" style="width:260px; margin:15px;"></div>

<p class="ui-state-default ui-corner-all" style="padding:4px;margin-top:4em;">
  <span class="ui-icon ui-icon-signal" style="float:left; margin:-2px 5px 0 0;"></span>
  图形均衡器
</p>

<div id="eq">
  <span>88</span>
  <span>77</span>
  <span>55</span>
  <span>33</span>
  <span>40</span>
  <span>45</span>
  <span>70</span>
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

- `多个滑块` 这一小节和 `滑块（Slider）` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
