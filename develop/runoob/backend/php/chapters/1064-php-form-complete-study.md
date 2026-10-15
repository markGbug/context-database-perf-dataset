# PHP：PHP 完整表单实例

- 来源：[PHP 完整表单实例](https://www.runoob.com/php/php-form-complete.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：学习笔记
- 章节序号：1064

## 本章内容

本章节将介绍如何让用户在点击"提交（submit）"按钮提交数据前保证所有字段正确输入。


## PHP - 在表单中确保输入值

在用户点击提交按钮后，为确保字段值是否输入正确，我们在HTML的input元素中插添加PHP脚本， 各字段名为: name, email, 和 website。 在备注中的 textarea 字段中，我们将脚本放于 <textarea> 和 </textarea> 标签之间。

PHP脚本输出值为： $name, $email, $website, 和 $comment 变量。

然后，我们同样需要检查被选中的单选按钮， 对于这一点，我们 必须设置好checked属性(不是radio按钮的 value 属性) :

```html
<form method="post" action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]);?>">
   名字: <input type="text" name="name" value="<?php echo $name;?>">
   <span class="error">* <?php echo $nameErr;?></span>
   <br><br>
   E-mail: <input type="text" name="email" value="<?php echo $email;?>">
   <span class="error">* <?php echo $emailErr;?></span>
   <br><br>
   网址: <input type="text" name="website" value="<?php echo $website;?>">
   <span class="error"><?php echo $websiteErr;?></span>
   <br><br>
   备注: <textarea name="comment" rows="5" cols="40"><?php echo $comment;?></textarea>
   <br><br>
   性别:
   <input type="radio" name="gender" <?php if (isset($gender) && $gender=="female") echo "checked";?>  value="female">女
   <input type="radio" name="gender" <?php if (isset($gender) && $gender=="male") echo "checked";?>  value="male">男
   <span class="error">* <?php echo $genderErr;?></span>
   <br><br>
   <input type="submit" name="submit" value="Submit">
</form>
```


## PHP - 完整表单实例

以下是完整的PHP表单验证实例代码：


## 实例

实例中执行结果类似如下图所示：


## 复习重点

- 能说明 `PHP 完整表单实例` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
