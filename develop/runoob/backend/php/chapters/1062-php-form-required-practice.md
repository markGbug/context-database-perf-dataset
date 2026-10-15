# PHP：PHP 表单 - 必需字段

- 来源：[PHP 表单 - 必需字段](https://www.runoob.com/php/php-form-required.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：练习笔记
- 章节序号：1062

## 本章内容

本章节我们将介绍如何设置表单必需字段及错误信息。


## PHP - 必需字段

在上一章节我们已经介绍了表的验证规则，我们可以看到"名字", "E-mail", 和 "性别" 字段是必需的，各字段不能为空。

如果在前面的章节中，所有输入字段都是可选的。

在以下代码中我们加入了一些新的变量: $nameErr, $emailErr, $genderErr, 和 $websiteErr.。这些错误变量将显示在必需字段上。 我们还为每个$_POST变量增加了一个if else语句。 这些语句将检查 $_POST 变量是 否为空（使用php的 empty() 函数）。如果为空，将显示对应的错误信息。 如果不为空，数据将传递给test_input() 函数：

```text
<?php
// 定义变量并默认设为空值
$nameErr = $emailErr = $genderErr = $websiteErr = "";
$name = $email = $gender = $comment = $website = "";

if ($_SERVER["REQUEST_METHOD"] == "POST") {
  if (empty($_POST["name"])) {
    $nameErr = "名字是必需的。";
  } else {
    $name = test_input($_POST["name"]);
  }

  if (empty($_POST["email"])) {
    $emailErr = "邮箱是必需的。";
  } else {
    $email = test_input($_POST["email"]);
  }

  if (empty($_POST["website"])) {
    $website = "";
  } else {
    $website = test_input($_POST["website"]);
  }

  if (empty($_POST["comment"])) {
    $comment = "";
  } else {
    $comment = test_input($_POST["comment"]);
  }

  if (empty($_POST["gender"])) {
    $genderErr = "性别是必需的。";
  } else {
    $gender = test_input($_POST["gender"]);
  }
}
?>
```


## PHP - 显示错误信息

在以下的HTML实例表单中，我们为每个字段中添加了一些脚本， 各个脚本会在信息输入错误时显示错误信息。(如果用户未填写信息就提交表单则会输出错误信息):

```html
<form method="post" action="<?php echo htmlspecialchars($_SERVER['PHP_SELF']);?>">
   名字: <input type="text" name="name">
   <span class="error">* <?php echo $nameErr;?></span>
   <br><br>
   E-mail: <input type="text" name="email">
   <span class="error">* <?php echo $emailErr;?></span>
   <br><br>
   网址: <input type="text" name="website">
   <span class="error"><?php echo $websiteErr;?></span>
   <br><br>
   备注: <textarea name="comment" rows="5" cols="40"></textarea>
   <br><br>
   性别:
   <input type="radio" name="gender" value="female">女
   <input type="radio" name="gender" value="male">男
   <span class="error">* <?php echo $genderErr;?></span>
   <br><br>
   <input type="submit" name="submit" value="Submit">
</form>
```

查看代码 »


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PHP 表单 - 必需字段` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
