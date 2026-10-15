# 知识点 82868：Highcharts：Highcharts 气泡图 - series.marker

- 来源：[Highcharts 气泡图](https://www.runoob.com/highcharts/highcharts-bubble-charts.html)
- 来源章节：[2581-highcharts-bubble-charts-study.md](../chapters/2581-highcharts-bubble-charts-study.md)
- 分类：前端开发
- 技术：Highcharts
- 所在小节：series.marker
- 知识类型：代码
- 原章节序号：2581

## 原文片段

```text
marker: {
   fillColor: {
      radialGradient: { cx: 0.4, cy: 0.3, r: 0.7 },
      stops: [
         [0, 'rgba(255,255,255,0.5)'],
         [1, Highcharts.Color(Highcharts.getOptions().colors[0]).setOpacity(0.5).get('rgba')]
      ]
   }
}
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `series.marker` 这一小节和 `Highcharts 气泡图` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
