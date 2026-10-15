# 知识点 82870：Highcharts：Highcharts 动态图 - chart.events

- 来源：[Highcharts 动态图](https://www.runoob.com/highcharts/highcharts-dynamic-click.html)
- 来源章节：[2582-highcharts-dynamic-click-study.md](../chapters/2582-highcharts-dynamic-click-study.md)
- 分类：前端开发
- 技术：Highcharts
- 所在小节：chart.events
- 知识类型：代码
- 原章节序号：2582

## 原文片段

```text
chart: {
   events: {
      click: function (e) {
         // 获取点击坐标和数据项
         var x = e.xAxis[0].value,
         y = e.yAxis[0].value,
         series = this.series[0];
         // 添加点击的坐标
         series.addPoint([x, y]);
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
