# 知识点 35181：CSS：CSS 下拉菜单 - 实例

- 来源：[CSS 下拉菜单](https://www.runoob.com/css/css-dropdowns.html)
- 来源章节：[2417-css-dropdowns-practice.md](../chapters/2417-css-dropdowns-practice.md)
- 分类：前端开发
- 技术：CSS
- 所在小节：实例
- 知识类型：代码
- 原章节序号：2417

## 原文片段

```text
<style>
.dropdown {
  position: relative;
  display: inline-block;
}
.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f9f9f9;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  padding: 12px 16px;
}
.dropdown:hover .dropdown-content {
  display: block;
}
</style>
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `实例` 这一小节和 `CSS 下拉菜单` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
