# 知识点 61575：PHP：PHP 安全 E-mail - PHP E-mail 注入

- 来源：[PHP 安全 E-mail](https://www.runoob.com/php/php-secure-mail.html)
- 来源章节：[1075-php-secure-mail-practice.md](../chapters/1075-php-secure-mail-practice.md)
- 分类：后端开发
- 技术：PHP
- 所在小节：PHP E-mail 注入
- 知识类型：解释
- 原章节序号：1075

## 原文片段

与往常一样，mail() 函数把上面的文本放入邮件头部，那么现在头部有了额外的 Cc:、Bcc: 和 To: 字段。当用户点击提交按钮时，这封 e-mail 会被发送到上面所有的地址！

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `PHP E-mail 注入` 这一小节和 `PHP 安全 E-mail` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
