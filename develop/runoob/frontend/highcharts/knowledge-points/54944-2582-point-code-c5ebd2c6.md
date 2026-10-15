# 知识点 54944：Highcharts：Highcharts 动态图 - 实例

- 来源：[Highcharts 动态图](https://www.runoob.com/highcharts/highcharts-dynamic-click.html)
- 来源章节：[2582-highcharts-dynamic-click-study.md](../chapters/2582-highcharts-dynamic-click-study.md)
- 分类：前端开发
- 技术：Highcharts
- 所在小节：实例
- 知识类型：代码
- 原章节序号：2582

## 原文片段

```text
<html>
<head>
<meta charset="UTF-8" />
<title>Highcharts 教程 | 菜鸟教程(runoob.com)</title>
<script src="http://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"></script>
<script src="http://code.highcharts.com/highcharts.js"></script></head>
<body>
<div id="container" style="width: 550px; height: 400px; margin: 0 auto"></div>
<script language="JavaScript">
$(document).ready(function() {
   var chart = {
      type: 'spline',
      animation: Highcharts.svg, // don't animate in IE < IE 10.
      marginRight: 10,
      events: {
         load: function () {
            // set up the updating of the chart each second
            var series = this.series[0];
            setInterval(function () {
               var x = (new Date()).getTime(), // current time
               y = Math.random();
               series.addPoint([x, y], true, true);
            }, 1000);
         }
      }
   };
   var title = {
      text: 'Live random data'
   };
   var xAxis = {
      type: 'datetime',
      tickPixelInterval: 150
   };
   var yAxis = {
      title: {
         text: 'Value'
      },
      plotLines: [{
         value: 0,
         width: 1,
         color: '#808080'
      }]
   };
   var tooltip = {
      formatter: function () {
      return '<b>' + this.series.name + '</b><br/>' +
         Highcharts.dateFormat('%Y-%m-%d %H:%M:%S', this.x) + '<br/>' +
         Highcharts.numberFormat(this.y, 2);
      }
   };
   var plotOptions = {
      area: {
         pointStart: 1940,
         marker: {
            enabled: false,
            symbol: 'circle',
            radius: 2,
            states: {
               hover: {
                 enabled: true
               }
            }
         }
      }
   };
   var legend = {
      enabled: false
   };
   var exporting = {
      enabled: false
   };
   var series= [{
      name: 'Random data',
      data: (function () {
         // generate an array of random data
         var data = [],time = (new Date()).getTime(),i;
         for (i = -19; i <= 0; i += 1) {
            data.push({
               x: time + i * 1000,
               y: Math.random()
            });
         }
         return data;
      }())
   }];

   var json = {};
   json.chart = chart;
   json.title = title;
   json.tooltip = tooltip;
   json.xAxis = xAxis;
   json.yAxis = yAxis;
   json.legend = legend;
   json.exporting = exporting;
   json.series = series;
   json.plotOptions = plotOptions;


   Highcharts.setOptions({
      global: {
         useUTC: false
      }
   });
   $('#container').highcharts(json);

});
</script>
</body>
</html>
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `实例` 这一小节和 `Highcharts 动态图` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
