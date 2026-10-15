# 知识点 83378：jQuery：jQuery JSONP - jsonp.php 文件代码

- 来源：[jQuery JSONP](https://www.runoob.com/json/json-jsonp.html)
- 来源章节：[2991-json-jsonp-study.md](../chapters/2991-json-jsonp-study.md)
- 分类：前端开发
- 技术：jQuery
- 所在小节：jsonp.php 文件代码
- 知识类型：代码
- 原章节序号：2991

## 原文片段

```text
<?php
header('Content-type: application/json');
//获取回调函数名
$jsoncallback = htmlspecialchars($_REQUEST ['jsoncallback']);
//json数据
$json_data = '["customername1","customername2"]';
//输出jsonp格式的数据
echo $jsoncallback . "(" . $json_data . ")";
?>
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `jsonp.php 文件代码` 这一小节和 `jQuery JSONP` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
