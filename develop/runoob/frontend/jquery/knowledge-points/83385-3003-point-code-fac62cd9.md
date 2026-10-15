# 知识点 83385：jQuery：jQuery Accordion - 带选项

- 来源：[jQuery Accordion](https://www.runoob.com/jquery/jquery-plugin-accordion.html)
- 来源章节：[3003-jquery-plugin-accordion-practice.md](../chapters/3003-jquery-plugin-accordion-practice.md)
- 分类：前端开发
- 技术：jQuery
- 所在小节：带选项
- 知识类型：代码
- 原章节序号：3003

## 原文片段

```text
jQuery('#list2').accordion({
    event: 'mouseover',
    active: '.selected',
    selectedClass: 'active',
    animated: "bounceslide",
    header: "dt"
}).bind("change.ui-accordion", function(event, ui) {
    jQuery('<div>' + ui.oldHeader.text() + ' hidden, ' + ui.newHeader.text() + ' shown</div>').appendTo('#log');
});
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `带选项` 这一小节和 `jQuery Accordion` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
