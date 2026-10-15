# 知识点 55204：HTML5：HTML5 Web Workers - 实例

- 来源：[HTML5 Web Workers](https://www.runoob.com/html/html5-webworkers.html)
- 来源章节：[2725-html5-webworkers-study.md](../chapters/2725-html5-webworkers-study.md)
- 分类：前端开发
- 技术：HTML5
- 所在小节：实例
- 知识类型：解释
- 原章节序号：2725

## 原文片段

开始 Worker 停止 Worker var w; function startWorker() { if(typeof(Worker)!=="undefined") { if(typeof(w)=="undefined") { w=new Worker("/try/demo_source/demo_workers.js"); } w.onmessage = function (event) { document.getElementById("result").innerHTML=event.data; }; } else { document.getElementById("result").innerHTML="抱歉，你的浏览器不支持 Web Workers..."; } } function stopWorker() { w.terminate(); w = undefined; }

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `实例` 这一小节和 `HTML5 Web Workers` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
