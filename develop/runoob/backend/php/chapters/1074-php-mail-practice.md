# PHP：PHP 发送电子邮件

- 来源：[PHP E-mail](https://www.runoob.com/php/php-mail.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：练习笔记
- 章节序号：1074

## 本章内容

PHP 允许您从脚本直接发送电子邮件。


## PHP mail() 函数

PHP mail() 函数用于从脚本中发送电子邮件。

语法

注释：PHP 运行邮件函数需要一个已安装且正在运行的邮件系统(如：sendmail、postfix、qmail等)。所用的程序通过在 php.ini 文件中的配置设置进行定义。请在我们的 PHP Mail 参考手册 阅读更多内容。


## PHP 简易 E-Mail

通过 PHP 发送电子邮件的最简单的方式是发送一封文本 email。

在下面的实例中，我们首先声明变量($to, $subject, $message, $from, $headers)，然后我们在 mail() 函数中使用这些变量来发送了一封 E-mail：

```text
<?php
$to = "someone@example.com";         // 邮件接收者
$subject = "参数邮件";                // 邮件标题
$message = "Hello! 这是邮件的内容。";  // 邮件正文
$from = "someonelse@example.com";   // 邮件发送者
$headers = "From:" . $from;         // 头部信息设置
mail($to,$subject,$message,$headers);
echo "邮件已发送";
?>
```


## PHP Mail 表单

通过 PHP，您能够在自己的站点制作一个反馈表单。下面的实例向指定的 e-mail 地址发送了一条文本消息：

```html
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<?php
if (isset($_REQUEST['email'])) { // 如果接收到邮箱参数则发送邮件
    // 发送邮件
    $email = $_REQUEST['email'] ;
    $subject = $_REQUEST['subject'] ;
    $message = $_REQUEST['message'] ;
    mail("someone@example.com", $subject,
    $message, "From:" . $email);
    echo "邮件发送成功";
} else { // 如果没有邮箱参数则显示表单
    echo "<form method='post' action='mailform.php'>
    Email: <input name='email' type='text'><br>
    Subject: <input name='subject' type='text'><br>
    Message:<br>
    <textarea name='message' rows='15' cols='40'>
    </textarea><br>
    <input type='submit'>
    </form>";
}
?>

</body>
</html>
```

- 首先，检查是否填写了邮件输入框
- 如果未填写（比如在页面被首次访问时），输出 HTML 表单
- 如果已填写（在表单被填写后），从表单发送电子邮件
- 当填写完表单点击提交按钮后，页面重新载入，可以看到邮件输入被重置，同时显示邮件发送成功的消息

注释：这个简易发送 e-mail 不安全，在本教程的下一章中，您将阅读到更多关于电子邮件脚本中的安全隐患，我们将为您讲解如何验证用户输入使它更安全。


## PHP Mail 参考手册

如需查看更多关于 PHP mail() 函数的信息，请访问我们的 PHP Mail 参考手册。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PHP E-mail` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
