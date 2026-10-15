# 知识点 83347：jQuery：jQuery 设置 - 实例

- 来源：[jQuery 设置](https://www.runoob.com/jquery/jquery-dom-set.html)
- 来源章节：[2976-jquery-dom-set-practice.md](../chapters/2976-jquery-dom-set-practice.md)
- 分类：前端开发
- 技术：jQuery
- 所在小节：实例
- 知识类型：代码
- 原章节序号：2976

## 原文片段

```text
$("#btn1").click(function(){
    $("#test1").text(function(i,origText){
        return "旧文本: " + origText + " 新文本: Hello world! (index: " + i + ")";
    });
});

$("#btn2").click(function(){
    $("#test2").html(function(i,origText){
        return "旧 html: " + origText + " 新 html: Hello <b>world!</b> (index: " + i + ")";
    });
});
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `实例` 这一小节和 `jQuery 设置` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
