# 知识点 89089：Node.js：Node.js 常用工具 - util.callbackify() - 将 Promise 转换为回调

- 来源：[Node.js 常用工具](https://www.runoob.com/nodejs/nodejs-util.html)
- 来源章节：[1021-nodejs-util-practice.md](../chapters/1021-nodejs-util-practice.md)
- 分类：后端开发
- 技术：Node.js
- 所在小节：util.callbackify() - 将 Promise 转换为回调
- 知识类型：解释
- 原章节序号：1021

## 原文片段

util.callbackify(original) 将 async 异步函数（或者一个返回值为 Promise 的函数）转换成遵循异常优先的回调风格的函数，例如将 (err, value) => ... 回调作为最后一个参数。在回调函数中，第一个参数为拒绝的原因（如果 Promise 解决，则为 null），第二个参数则是解决的值。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `util.callbackify() - 将 Promise 转换为回调` 这一小节和 `Node.js 常用工具` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
