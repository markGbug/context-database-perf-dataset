# 知识点 35511：Highcharts：Highcharts 动态图 - chart.events

- 来源：[Highcharts 动态图](https://www.runoob.com/highcharts/highcharts-dynamic-click.html)
- 来源章节：[2582-highcharts-dynamic-click-practice.md](../chapters/2582-highcharts-dynamic-click-practice.md)
- 分类：前端开发
- 技术：Highcharts
- 所在小节：chart.events
- 知识类型：代码
- 原章节序号：2582

## 原文片段

```text
chart: {
   events: {
      load: function () {
         // 图表每秒更新一次
         var series = this.series[0];
         setInterval(function () {
            var x = (new Date()).getTime(), // 当期时间
            y = Math.random();
            series.addPoint([x, y], true, true);
         }, 1000);
      }
   }
}
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `chart.events` 这一小节和 `Highcharts 动态图` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
