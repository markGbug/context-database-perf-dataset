# 知识点 64429：Highcharts：Highcharts 气泡图 - 实例

- 来源：[Highcharts 气泡图](https://www.runoob.com/highcharts/highcharts-bubble-charts.html)
- 来源章节：[2581-highcharts-bubble-charts-practice.md](../chapters/2581-highcharts-bubble-charts-practice.md)
- 分类：前端开发
- 技术：Highcharts
- 所在小节：实例
- 知识类型：代码
- 原章节序号：2581

## 原文片段

```text
<html>
<head>
<meta charset="UTF-8" />
<title>Highcharts 教程 | 菜鸟教程(runoob.com)</title>
<script src="http://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"></script>
<script src="http://code.highcharts.com/highcharts.js"></script>
<script src="http://code.highcharts.com/highcharts-more.js"></script>
</head>
<body>
<div id="container" style="width: 550px; height: 400px; margin: 0 auto"></div>
<script language="JavaScript">
$(document).ready(function() {
   var chart = {
      type: 'bubble',
      zoomType: 'xy'
   };
   var title = {
      text: 'Highcharts Bubbles'
   };
   var series= [{
            data: [[97, 36, 79], [94, 74, 60], [68, 76, 58], [64, 87, 56], [68, 27, 73], [74, 99, 42], [7, 93, 87], [51, 69, 40], [38, 23, 33], [57, 86, 31]]
        }, {
            data: [[25, 10, 87], [2, 75, 59], [11, 54, 8], [86, 55, 93], [5, 3, 58], [90, 63, 44], [91, 33, 17], [97, 3, 56], [15, 67, 48], [54, 25, 81]]
        }, {
            data: [[47, 47, 21], [20, 12, 4], [6, 76, 91], [38, 30, 60], [57, 98, 64], [61, 17, 80], [83, 60, 13], [67, 78, 75], [64, 12, 10], [30, 77, 82]]
      }
   ];

   var json = {};
   json.chart = chart;
   json.title = title;
   json.series = series;
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

- `实例` 这一小节和 `Highcharts 气泡图` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
