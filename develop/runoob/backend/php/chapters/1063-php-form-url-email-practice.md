# PHP：PHP 表单 - 验证邮件和URL

- 来源：[PHP 表单 - 验证邮件和URL](https://www.runoob.com/php/php-form-url-email.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：练习笔记
- 章节序号：1063

## 本章内容

本章节我们将介绍如何验证 names(名称), e-mails（邮件）, 和 URLs。


## PHP - 验证名称

以下代码将通过简单的方式来检测 name 字段是否包含字母和空格，如果 name 字段值不合法，将输出错误信息：

```text
$name = test_input($_POST["name"]);
if (!preg_match("/^[a-zA-Z ]*$/",$name)) {
  $nameErr = "只允许字母和空格";
}
```

int preg_match ( string $pattern , string $subject [, array $matches [, int $flags ]] )


## PHP - 验证邮件

以下代码将通过简单的方式来检测 e-mail 地址是否合法。如果 e-mail 地址不合法，将输出错误信息：

```text
$email = test_input($_POST["email"]);
if (!preg_match("/([\w\-]+\@[\w\-]+\.[\w\-]+)/",$email)) {
  $emailErr = "非法邮箱格式";
}
```


## PHP - 验证 URL

以下代码将检测URL地址是否合法 (以下正则表达式运行URL中含有破折号:"-")， 如果 URL 地址不合法，将输出错误信息：

```text
$website = test_input($_POST["website"]);
if (!preg_match("/\b(?:(?:https?|ftp):\/\/|www\.)[-a-z0-9+&@#\/%?=~_|!:,.;]*[-a-z0-9+&@#\/%=~_|]/i",$website)) {
  $websiteErr = "非法的 URL 的地址";
}
```


## PHP - 验证 Name, E-mail, 和 URL

代码如下所示:

```text
<?php
// 定义变量并默认设置为空值
$nameErr = $emailErr = $genderErr = $websiteErr = "";
$name = $email = $gender = $comment = $website = "";

if ($_SERVER["REQUEST_METHOD"] == "POST") {
   if (empty($_POST["name"])) {
      $nameErr = "Name is required";
      } else {
         $name = test_input($_POST["name"]);
         // 检测名字是否只包含字母跟空格
         if (!preg_match("/^[a-zA-Z ]*$/",$name)) {
         $nameErr = "只允许字母和空格";
         }
     }

   if (empty($_POST["email"])) {
      $emailErr = "Email is required";
   } else {
      $email = test_input($_POST["email"]);
      // 检测邮箱是否合法
      if (!preg_match("/([\w\-]+\@[\w\-]+\.[\w\-]+)/",$email)) {
         $emailErr = "非法邮箱格式";
      }
   }

   if (empty($_POST["website"])) {
      $website = "";
   } else {
      $website = test_input($_POST["website"]);
      // 检测 URL 地址是否合法
     if (!preg_match("/\b(?:(?:https?|ftp):\/\/|www\.)[-a-z0-9+&@#\/%?=~_|!:,.;]*[-a-z0-9+&@#\/%=~_|]/i",$website)) {
         $websiteErr = "非法的 URL 的地址";
      }
   }

   if (empty($_POST["comment"])) {
      $comment = "";
   } else {
      $comment = test_input($_POST["comment"]);
   }

   if (empty($_POST["gender"])) {
      $genderErr = "性别是必需的";
   } else {
      $gender = test_input($_POST["gender"]);
   }
}
?>
```

运行实例 »


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PHP 表单 - 验证邮件和URL` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
