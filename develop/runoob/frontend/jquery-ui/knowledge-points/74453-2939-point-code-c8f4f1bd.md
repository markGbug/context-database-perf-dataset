# 知识点 74453：jQuery UI：排序（Sortable） - 标签页连接列表

- 来源：[排序（Sortable）](https://www.runoob.com/jqueryui/example-sortable.html)
- 来源章节：[2939-example-sortable-study.md](../chapters/2939-example-sortable-study.md)
- 分类：前端开发
- 技术：jQuery UI
- 所在小节：标签页连接列表
- 知识类型：代码
- 原章节序号：2939

## 原文片段

```text
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>jQuery UI 排序（Sortable） - 标签页连接列表</title>
  <link rel="stylesheet" href="//code.jquery.com/ui/1.10.4/themes/smoothness/jquery-ui.css">
  <script src="//code.jquery.com/jquery-1.9.1.js"></script>
  <script src="//code.jquery.com/ui/1.10.4/jquery-ui.js"></script>
  <link rel="stylesheet" href="http://jqueryui.com/resources/demos/style.css">
  <style>
  #sortable1 li, #sortable2 li { margin: 0 5px 5px 5px; padding: 5px; font-size: 1.2em; width: 120px; }
  </style>
  <script>
  $(function() {
    $( "#sortable1, #sortable2" ).sortable().disableSelection();

    var $tabs = $( "#tabs" ).tabs();

    var $tab_items = $( "ul:first li", $tabs ).droppable({
      accept: ".connectedSortable li",
      hoverClass: "ui-state-hover",
      drop: function( event, ui ) {
        var $item = $( this );
        var $list = $( $item.find( "a" ).attr( "href" ) )
          .find( ".connectedSortable" );

        ui.draggable.hide( "slow", function() {
          $tabs.tabs( "option", "active", $tab_items.index( $item ) );
          $( this ).appendTo( $list ).show( "slow" );
        });
      }
    });
  });
  </script>
</head>
<body>

<div id="tabs">
  <ul>
    <li><a href="#tabs-1">Nunc tincidunt</a></li>
    <li><a href="#tabs-2">Proin dolor</a></li>
  </ul>
  <div id="tabs-1">
    <ul id="sortable1" class="connectedSortable ui-helper-reset">
      <li class="ui-state-default">Item 1</li>
      <li class="ui-state-default">Item 2</li>
      <li class="ui-state-default">Item 3</li>
      <li class="ui-state-default">Item 4</li>
      <li class="ui-state-default">Item 5</li>
    </ul>
  </div>
  <div id="tabs-2">
    <ul id="sortable2" class="connectedSortable ui-helper-reset">
      <li class="ui-state-highlight">Item 1</li>
      <li class="ui-state-highlight">Item 2</li>
      <li class="ui-state-highlight">Item 3</li>
      <li class="ui-state-highlight">Item 4</li>
      <li class="ui-state-highlight">Item 5</li>
    </ul>
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

- `标签页连接列表` 这一小节和 `排序（Sortable）` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
