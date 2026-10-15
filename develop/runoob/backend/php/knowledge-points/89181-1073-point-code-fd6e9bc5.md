# 知识点 89181：PHP：PHP Session - 实例

- 来源：[PHP Session](https://www.runoob.com/php/php-sessions.html)
- 来源章节：[1073-php-sessions-practice.md](../chapters/1073-php-sessions-practice.md)
- 分类：后端开发
- 技术：PHP
- 所在小节：实例
- 知识类型：代码
- 原章节序号：1073

## 原文片段

```text
<?php
session_start();
// 存储 session 数据
$_SESSION['views']=1;
?>

<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<?php
// 检索 session 数据
echo "浏览量：". $_SESSION['views'];
?>

</body>
</html>
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `实例` 这一小节和 `PHP Session` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
