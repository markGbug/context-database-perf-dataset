# jQuery UI：jQuery UI 实例 - 颜色动画（Color Animation）

- 来源：[颜色动画](https://www.runoob.com/jqueryui/example-animate.html)
- 分类：前端开发
- 技术：jQuery UI
- 笔记类型：练习笔记
- 章节序号：2959

## 本章内容

使用 .animate() 实现颜色动画效果。

如需了解更多有关颜色动画（Color Animation）的细节，请查看 API 文档 颜色动画（Color Animation）。

jQuery UI 捆绑了 jQuery Color 插件，jQuery Color 插件提供了颜色动画及其他许多与颜色相关的实用功能。


## 动画（Animation）演示

点击按钮预览特效。

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>jQuery UI 特效 - 动画（Animation）演示</title>
  <link rel="stylesheet" href="//code.jquery.com/ui/1.10.4/themes/smoothness/jquery-ui.css">
  <script src="//code.jquery.com/jquery-1.9.1.js"></script>
  <script src="//code.jquery.com/ui/1.10.4/jquery-ui.js"></script>
  <link rel="stylesheet" href="http://jqueryui.com/resources/demos/style.css">
  <style>
    .toggler { width: 500px; height: 200px; position: relative; }
    #button { padding: .5em 1em; text-decoration: none; }
    #effect { width: 240px; height: 135px; padding: 0.4em; position: relative; background: #fff; }
    #effect h3 { margin: 0; padding: 0.4em; text-align: center; }
  </style>
  <script>
  $(function() {
    var state = true;
    $( "#button" ).click(function() {
      if ( state ) {
        $( "#effect" ).animate({
          backgroundColor: "#aa0000",
          color: "#fff",
          width: 500
        }, 1000 );
      } else {
        $( "#effect" ).animate({
          backgroundColor: "#fff",
          color: "#000",
          width: 240
        }, 1000 );
      }
      state = !state;
    });
  });
  </script>
</head>
<body>

<div class="toggler">
  <div id="effect" class="ui-widget-content ui-corner-all">
    <h3 class="ui-widget-header ui-corner-all">动画（Animation）</h3>
    <p>
      Etiam libero neque, luctus a, eleifend nec, semper at, lorem. Sed pede. Nulla lorem metus, adipiscing ut, luctus sed, hendrerit vitae, mi.
    </p>
  </div>
</div>

<a href="#" id="button" class="ui-state-default ui-corner-all">切换特效</a>


</body>
</html>
```

查看演示


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `颜色动画` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
