# 知识点 54396：AngularJS：AngularJS 模型 - AngularJS 实例

- 来源：[AngularJS 模型](https://www.runoob.com/angularjs/angularjs-model.html)
- 来源章节：[2281-angularjs-model-study.md](../chapters/2281-angularjs-model-study.md)
- 分类：前端开发
- 技术：AngularJS
- 所在小节：AngularJS 实例
- 知识类型：代码
- 原章节序号：2281

## 原文片段

```text
<form ng-app="" name="myForm" ng-init="myText = 'test@runoob.com'">

Email:
<input type="email" name="myAddress" ng-model="myText" required>
<p>编辑邮箱地址，查看状态的改变。</p>
<h1>状态</h1>
<p>Valid: {{myForm.myAddress.$valid}} (如果输入的值是合法的则为 true)。</p>
<p>Dirty: {{myForm.myAddress.$dirty}} (如果值改变则为 true)。</p>
<p>Touched: {{myForm.myAddress.$touched}} (如果通过触屏点击则为 true)。</p>
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `AngularJS 实例` 这一小节和 `AngularJS 模型` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
