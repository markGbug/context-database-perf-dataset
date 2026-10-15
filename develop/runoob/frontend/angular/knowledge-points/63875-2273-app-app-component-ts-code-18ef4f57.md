# 知识点 63875：Angular：Angular 2 数据显示 - app/app.component.ts 文件：

- 来源：[Angular 2 数据显示](https://www.runoob.com/angularjs2/angularjs2-displaying-data.html)
- 来源章节：[2273-angularjs2-displaying-data-practice.md](../chapters/2273-angularjs2-displaying-data-practice.md)
- 分类：前端开发
- 技术：Angular
- 所在小节：app/app.component.ts 文件：
- 知识类型：代码
- 原章节序号：2273

## 原文片段

```text
import { Component } from '@angular/core';
@Component({
  selector: 'my-app',
  template: `
    <h1>{{title}}</h1>
    <h2>我喜欢的网站: {{mySite}}</h2>
    `
})
export class AppComponent {
  title = '站点列表';
  mySite = '菜鸟教程';
}
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `app/app.component.ts 文件：` 这一小节和 `Angular 2 数据显示` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
