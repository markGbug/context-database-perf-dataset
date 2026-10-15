# 知识点 89157：PHP：PHP 表单 - php_form_select.php 文件代码：

- 来源：[PHP 表单](https://www.runoob.com/php/php-forms.html)
- 来源章节：[1060-php-forms-practice.md](../chapters/1060-php-forms-practice.md)
- 分类：后端开发
- 技术：PHP
- 所在小节：php_form_select.php 文件代码：
- 知识类型：代码
- 原章节序号：1060

## 原文片段

```text
<?php
$q = isset($_GET['q'])? htmlspecialchars($_GET['q']) : '';
if($q) {
        if($q =='RUNOOB') {
                echo '菜鸟教程<br>http://www.runoob.com';
        } else if($q =='GOOGLE') {
                echo 'Google 搜索<br>http://www.google.com';
        } else if($q =='TAOBAO') {
                echo '淘宝<br>http://www.taobao.com';
        }
} else {
?>
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `php_form_select.php 文件代码：` 这一小节和 `PHP 表单` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
