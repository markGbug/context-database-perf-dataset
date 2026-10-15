# jQuery UI：jQuery UI 实例 - 进度条（Progressbar）

- 来源：[进度条（Progressbar）](https://www.runoob.com/jqueryui/example-progressbar.html)
- 分类：前端开发
- 技术：jQuery UI
- 笔记类型：练习笔记
- 章节序号：2946

## 本章内容

显示一个确定的或不确定的进程状态。

如需了解更多有关 progressbar 部件的细节，请查看 API 文档 进度条部件（Progressbar Widget）。


## 默认功能

默认的确定的进度条。

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>jQuery UI 进度条（Progressbar） - 默认功能</title>
  <link rel="stylesheet" href="//code.jquery.com/ui/1.10.4/themes/smoothness/jquery-ui.css">
  <script src="//code.jquery.com/jquery-1.9.1.js"></script>
  <script src="//code.jquery.com/ui/1.10.4/jquery-ui.js"></script>
  <link rel="stylesheet" href="http://jqueryui.com/resources/demos/style.css">
  <script>
  $(function() {
    $( "#progressbar" ).progressbar({
      value: 37
    });
  });
  </script>
</head>
<body>

<div id="progressbar"></div>


</body>
</html>
```

查看演示


## 自定义标签

自定义更新的标签。

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>jQuery UI 进度条（Progressbar） - 自定义标签</title>
  <link rel="stylesheet" href="//code.jquery.com/ui/1.10.4/themes/smoothness/jquery-ui.css">
  <script src="//code.jquery.com/jquery-1.9.1.js"></script>
  <script src="//code.jquery.com/ui/1.10.4/jquery-ui.js"></script>
  <link rel="stylesheet" href="http://jqueryui.com/resources/demos/style.css">
  <style>
  .ui-progressbar {
    position: relative;
  }
  .progress-label {
    position: absolute;
    left: 50%;
    top: 4px;
    font-weight: bold;
    text-shadow: 1px 1px 0 #fff;
  }
  </style>
  <script>
  $(function() {
    var progressbar = $( "#progressbar" ),
      progressLabel = $( ".progress-label" );

    progressbar.progressbar({
      value: false,
      change: function() {
        progressLabel.text( progressbar.progressbar( "value" ) + "%" );
      },
      complete: function() {
        progressLabel.text( "完成！" );
      }
    });

    function progress() {
      var val = progressbar.progressbar( "value" ) || 0;

      progressbar.progressbar( "value", val + 1 );

      if ( val < 99 ) {
        setTimeout( progress, 100 );
      }
    }

    setTimeout( progress, 3000 );
  });
  </script>
</head>
<body>

<div id="progressbar"><div class="progress-label">加载...</div></div>


</body>
</html>
```

查看演示


## 不确定的值

不确定的进度条，并可在确定和不确定的样式之间切换。

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>jQuery UI 进度条（Progressbar） - 不确定的值</title>
  <link rel="stylesheet" href="//code.jquery.com/ui/1.10.4/themes/smoothness/jquery-ui.css">
  <script src="//code.jquery.com/jquery-1.9.1.js"></script>
  <script src="//code.jquery.com/ui/1.10.4/jquery-ui.js"></script>
  <link rel="stylesheet" href="http://jqueryui.com/resources/demos/style.css">
  <script>
  $(function() {
    $( "#progressbar" ).progressbar({
      value: false
    });
    $( "button" ).on( "click", function( event ) {
      var target = $( event.target ),
        progressbar = $( "#progressbar" ),
        progressbarValue = progressbar.find( ".ui-progressbar-value" );

      if ( target.is( "#numButton" ) ) {
        progressbar.progressbar( "option", {
          value: Math.floor( Math.random() * 100 )
        });
      } else if ( target.is( "#colorButton" ) ) {
        progressbarValue.css({
          "background": '#' + Math.floor( Math.random() * 16777215 ).toString( 16 )
        });
      } else if ( target.is( "#falseButton" ) ) {
        progressbar.progressbar( "option", "value", false );
      }
    });
  });
  </script>
  <style>
  #progressbar .ui-progressbar-value {
    background-color: #ccc;
  }
  </style>
</head>
<body>

<div id="progressbar"></div>
<button id="numButton">随机值 - 确定</button>
<button id="falseButton">不确定</button>
<button id="colorButton">随机颜色</button>


</body>
</html>
```

查看演示


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `进度条（Progressbar）` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
