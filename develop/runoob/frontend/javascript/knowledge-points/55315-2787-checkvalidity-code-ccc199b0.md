# 知识点 55315：JavaScript：JavaScript 验证 API - checkValidity() 方法

- 来源：[JavaScript 验证 API](https://www.runoob.com/js/js-validation-api.html)
- 来源章节：[2787-js-validation-api-practice.md](../chapters/2787-js-validation-api-practice.md)
- 分类：前端开发
- 技术：JavaScript
- 所在小节：checkValidity() 方法
- 知识类型：代码
- 原章节序号：2787

## 原文片段

```text
function myFunction() {
    var inpObj = document.getElementById("id1");
    if (inpObj.checkValidity() == false) {
        document.getElementById("demo").innerHTML = inpObj.validationMessage;
    }
}
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `checkValidity() 方法` 这一小节和 `JavaScript 验证 API` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
