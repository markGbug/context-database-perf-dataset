# jQuery UI：jQuery UI 实例 - 转换 Class（Switch Class）

- 来源：[.switchClass()](https://www.runoob.com/jqueryui/example-switchclass.html)
- 分类：前端开发
- 技术：jQuery UI
- 笔记类型：练习笔记
- 章节序号：2958

## 本章内容

当动画样式改变时，为匹配的元素集合内的每个元素添加和移除指定的 Class。

如需了解更多有关 .switchClass() 方法的细节，请查看 API 文档 .switchClass()。


## .switchClass() 演示

点击按钮预览特效。

```html
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

查看演示


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `.switchClass()` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
