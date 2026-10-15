# 知识点 88706：Docker：Docker 安装 PHP - Nginx + PHP 部署

- 来源：[Docker 安装 PHP](https://www.runoob.com/docker/docker-install-php.html)
- 来源章节：[0814-docker-install-php-study.md](../chapters/0814-docker-install-php-study.md)
- 分类：后端开发
- 技术：Docker
- 所在小节：Nginx + PHP 部署
- 知识类型：代码
- 原章节序号：0814

## 原文片段

```text
$ docker run --name  myphp-fpm -v ~/nginx/www:/www  -d php:5.6-fpm
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `Nginx + PHP 部署` 这一小节和 `Docker 安装 PHP` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
