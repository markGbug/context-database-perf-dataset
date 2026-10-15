# PHP：PHP 完整表单实例

- 来源：[PHP 完整表单实例](https://www.runoob.com/php/php-form-complete.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：练习笔记
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


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PHP 完整表单实例` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
